task :default => 'tags:generate'

# Found at: http://gist.github.com/143571
namespace :tags do
  task :generate do
    puts 'Generating tags...'
    require 'rubygems'
    require 'jekyll'
    include Jekyll::Filters
 
    options = Jekyll.configuration({})
    site = Jekyll::Site.new(options)
    site.read_posts('')
 
    html =<<-HTML
---
layout: default
title: Tags
---
  
    HTML
 
    # Sort by the number of posts in the category.
    categories = site.categories.sort_by { |s| s[1].length }

    categories.reverse.each do |category, posts|
      html << <<-HTML
      <h3 id="#{category}">#{category}</h3>
      HTML
 
      html << '<ul class="posts">'
      posts.reverse.each do |post|
        post_data = post.to_liquid
        html << <<-HTML    
          <li><span>#{date_to_string post.date}</span> &rarr; <a href="#{post.url}">#{post_data['title']}</a></li>
        HTML
      end
      html << '</ul>'
    end
 
    File.open('tags.html', 'w+') do |file|
      file.puts html
    end
 
    puts 'Done.'
  end
end