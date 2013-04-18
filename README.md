#this is for github practice
###things that could use additions for better awesomeness
* a better way to place the saved files instead of the root folder where you run the script
* a view
* options to scrape different things
* a better name

```ruby
require 'rubygems'
require 'nokogiri'
require 'open-uri'
require 'uri'

puts "what website would you like to scrape?"
link = gets.chomp
URL = link

def make_absolute( href, root )
  URI.parse(root).merge(URI.parse(href)).to_s
end

Nokogiri::HTML(open(URL)).xpath("//img/@src").each do |src|
  uri = make_absolute(src,URL)
  File.open(File.basename(uri),'wb'){ |f|p f.methods; f.write(open(uri).read) }
end
```
