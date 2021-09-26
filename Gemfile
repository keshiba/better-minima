# frozen_string_literal: true

source "https://rubygems.org"
gemspec

gem "jekyll", ENV["JEKYLL_VERSION"] if ENV["JEKYLL_VERSION"]
gem 'wdm', '>= 0.1.0' if Gem.win_platform?
gem 'jekyll-paginate', '>= 1.1.0'
gem "kramdown-parser-gfm" if ENV["JEKYLL_VERSION"] == "~> 3.9"
