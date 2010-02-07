--- 
title: Dynamic DNS with DHCP and BIND 9
layout: post
---
<div class="item">
          
        
            <p>Unfortunately, getting DHCP3 and BIND9 to work together is not quite
	  as easy as it could/should be. I found it really difficult to find any
	  decent examples, and the docs weren't much use. DHCP's man page fails to
	  actually explicitly tell you about certain options, instead you have to
	  guess them from the text. I've put this here in the hope that it might be
	  handy to some of you.</p>

  	  <h2>Config Files</h2>
	  <p>The main two config files are <code>dhcpd.conf</code> and
	  <code>named.conf</code>. Here they are:</p>

<pre>		

# /etc/dhcp/dhcpd.conf
################################################################## 

server-identifier 192.168.0.9; # Should be the IP address of the DHCP server
# thanks to Aaron for pointing this out.
authoritative;
# this is the most important line. It specifies the method
# to use to connect to the DNS server and update it.

ddns-update-style interim;

# this has to be the same key as is used in named.conf
key mykey {
	algorithm hmac-md5;
	secret "secret_md5_hash";
};
# this section describes what key to use in what zone
zone example.com. {
	primary 192.168.0.9;
key mykey;
}
zone 0.168.192.in-addr.arpa. {
	primary 192.168.0.9;
key mykey;
}
# and this section holds all the options for the subnet listed,
# including the range of addresses to lease out, gateways etc.
subnet 192.168.0.0 netmask 255.255.255.0 {
	&nbsp;&nbsp;# use these addresses:
	&nbsp;&nbsp;range 192.168.0.10 192.168.0.20;
	&nbsp;&nbsp;option subnet-mask 255.255.255.0;
	&nbsp;&nbsp;option broadcast-address 192.168.0.255;
	&nbsp;&nbsp;option domain-name "example.com";
	&nbsp;&nbsp;one-lease-per-client on;
	&nbsp;&nbsp;default-lease-time 14400;
	&nbsp;&nbsp;max-lease-time 14401;
	&nbsp;&nbsp;option ip-forwarding off;
	&nbsp;&nbsp;option time-offset -18000;
	&nbsp;&nbsp;# set a few handy default options
	&nbsp; option routers 192.168.0.9;
	&nbsp;&nbsp;option domain-name-servers 192.168.0.9;
	&nbsp;&nbsp;option smtp-server 192.168.0.9;
	&nbsp;&nbsp;option netbios-name-servers 192.168.0.9;
}
################################################################## 

</pre>

<pre>	
////////////////////////////////////////////////////////////////// 
// /etc/bind/named.conf
////////////////////////////////////////////////////////////////// 

// First off is the key. To modify the running DNS server you need
// this, the same as in the dhcpd.conf file.
key mykey {
&nbsp;&nbsp;algorithm hmac-md5;
&nbsp;&nbsp;secret "secret_md5_hash";
};
// Next the access control section, we allow the 192.168.0.0-255
// subnet, and localhost.
acl "home" { 192.168.0.0/24; 127.0.0.1;};
// Some general options, including who to forward queries you can't 
// resolve to. (in this case they are claranet's dns servers.)
options {
&nbsp;&nbsp;directory "/var/bind/"; //Working directory
&nbsp;&nbsp;pid-file "/var/run/named/named.pid"; 

&nbsp;&nbsp;allow-query { "home"; };
&nbsp;&nbsp;forwarders { 195.8.69.7; 195.8.69.12; };
};
// You need this section to allow the communication between
// daemons. (dhcp and bind)
controls {
&nbsp;&nbsp;inet 127.0.0.1 port 953

&nbsp;&nbsp;allow { 127.0.0.1; 192.168.0.9; } keys { "mykey"; 
};
};
// And then you have pretty much standard zones, except for the
// fact that the key specified at the top is allowed to modify the 
// domain zone and reverse zone at the bottom.
zone "0.0.127.in-addr.arpa" {
&nbsp;&nbsp;type master;
&nbsp;&nbsp;file "localhost.rev";
&nbsp;&nbsp;notify no;
};
zone "example.com" {

&nbsp;&nbsp;type master;
&nbsp;&nbsp;notify no;
&nbsp;&nbsp;file "/var/bind</b>/example.com";
&nbsp;&nbsp;allow-update { key mykey; };
};
zone "0.168.192.in-addr.arpa"{
&nbsp;&nbsp;type master;
&nbsp;&nbsp;notify no;
&nbsp;&nbsp;file "/var/bind/example.com.rev";
&nbsp;&nbsp;allow-update { key mykey; };
};
zone "." {

&nbsp;&nbsp;type hint;

&nbsp;&nbsp;file "named.ca";
};
////////////////////////////////////////////////////////////////// 
</pre>

<p>You can generate the keys with <code>dnssec-keygen</code>, 
and you may well need to use 
<code>rndc-confgen</code> to generate the config for rndc, the dns control 
program.  You should make sure you use the same md5 key in that as well.</p>

<h2>Zone Files</h2>

<p>Originally, I didn't include my zone files here, mainly due to a lack of
understanding.  I've now got the DNS and BIND O'Reilly book though, and have
discovered that things are actually fairly simple.</p>

<p>Here is my <code>home.hosts</code> file.
</p><pre>;
; SOA: Start of authority record - this NS is the best source of info in this
; zone (See DNS and Bind book, ch 4.)
;
$ORIGIN .
$TTL 86400  ; 1 day
example.com.	IN SOA	example.com. nadir.example.com. (
				2000111383 ; serial
				10800      ; refresh (3 hours)
				3600       ; retry (1 hour)
				604800     ; expire (1 week)
				86400      ; minimum (1 day)
				)
;
; Name servers: same domain name as origin. 
;
				IN NS	nadir.example.com.

;
; Name to address mappings follow. Address to name mappings can be found in
; home.hosts.rev
;
; Put any addresses you want fixed here. Dynamically set addresses will appear
; below.
; 
nadir.example.com	IN A	192.168.0.254
</pre>

<p>Here is <code>home.hosts.rev</code>
</p><pre>;
; SOA section: like above only maps addresses to names.
;
$ORIGIN .
$TTL 86400  ; 1 day
0.168.192.in-addr.arpa	IN SOA	example.com. nadir.example.com. (
				2000107274 ; serial
				28800      ; refresh (8 hours)
				14400      ; retry (4 hours)
				3024000    ; expire (5 weeks)
				86400      ; minimum (1 day)
				)
;
; Name Servers
;
			IN NS	nadir.example.com.

;
; Fixed addresses, followed by DDNS inserted mappings. 
;
254.0.168.192.in-addr.arpa. PTR nadir.example.com.

</pre>

  <p>This setup works for me, and allows both forward and reverse lookups.</p>

  <h2>Troubleshooting</h2>
  <p>What to do if DNS fails to update:</p>
  <ul>
	<li>Check that BIND has write permissions for the directory where you've
	put the zone files. On my box, that's <code>/var/<b style="color: black; background-color: rgb(160, 255, 255);">bind</b></code>. (Thanks Alex!)</li>

	<li>Make sure your DHCP client sends it's hostname. Windows boxes do this
	anyway, but lots of unix clients need to be told. So, for pump users, you need to
	do <code>pump -h hostname</code>. If you use dhclient, then make sure you have a
	line reading:
	<pre>send host-name "hostname"</pre> in your <code>dhclient.conf</code>.</li>
  </ul>
	
  
  <h2>Finally</h2>
  <p>I'm no expert, and I may well have done something very stupid, 
  or missed something  altogether. Please tell me if I have, and I'll tweak this.
  I used the domain example.com for security reasons, and because everyone else 
  does. Have fun :-)</p>

        
          
            </div>
