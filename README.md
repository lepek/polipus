[![Build Status](https://travis-ci.org/taganaka/polipus.svg?branch=master)](https://travis-ci.org/taganaka/polipus)
[![Coverage Status](https://img.shields.io/coveralls/taganaka/polipus/master.svg)](https://coveralls.io/r/taganaka/polipus?branch=master)
[![Code Climate](https://codeclimate.com/github/taganaka/polipus.svg)](https://codeclimate.com/github/taganaka/polipus)
[![RubyGems](http://img.shields.io/gem/v/polipus.svg)](https://rubygems.org/gems/polipus)

# Polipus #

A distributed web crawler written in ruby, backed by Redis
This project has been presented to the RubyDay2013
http://www.slideshare.net/francescolaurita/roll-your-own-web-crawler-rubyday

## Features ##

* Easy to use
* Distributed and scalable
* It uses a smart/fast and space-efficient probabilistic data structure to determine if an url should be visited or not
* It doesn't exaust your Redis server
* Play nicely with MongoDB even if it is not strictly required
* Easy to write your own page storage strategy
* Focus crawling made easy
* Heavily inspired to Anemone https://github.com/chriskite/anemone/

## Supported Ruby Interpreters

* MRI 1.9.x >= 1.9.1
* MRI 2.0.0
* MRI 2.1.2
* JRuby 1.9 mode
* Rubinius


## Survival code example

```ruby
require "polipus"

Polipus.crawler("rubygems","http://rubygems.org/") do |crawler|
  # In-place page processing
  crawler.on_page_downloaded do |page|
    # A nokogiri object
    puts "Page title: '#{page.doc.css('title').text}' Page url: #{page.url}"
  end
end
```

## Installation

    $ gem install polipus

## Testing

    $ bundle install
    $ rake

## Contributing to polipus ##
 
* Check out the latest master to make sure the feature hasn't been implemented or the bug hasn't been fixed yet.
* Check out the issue tracker to make sure someone already hasn't requested it and/or contributed it.
* Fork the project.
* Start a feature/bugfix branch.
* Commit and push until you are happy with your contribution.
* Make sure to add tests for it. This is important so I don't break it in a future version unintentionally.
* Install [Rubocop](https://github.com/bbatsov/rubocop) and make sure it is happy
* Please try not to mess with the Rakefile, version, or history. If you want to have your own version, or is otherwise necessary, that is fine, but please isolate to its own commit so I can cherry-pick around it.

## Copyright ##

Copyright (c) 2013 Francesco Laurita. See LICENSE.txt for
further details.

