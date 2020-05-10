# better-minima

[![Gem Version](https://badge.fury.io/rb/better-minima.svg)](https://badge.fury.io/rb/better-minima)

*Better-Minima* is based on [Minima](https://github.com/jekyll/minima) which is Jekyll's default theme.
Minima is a beautiful theme to begin with and has a clean look. 

Better-Minima builds upon it by making the theme more suitable for a personal blog.

[Theme preview](http://keshiba.me)

![better-minima theme preview](https://raw.githubusercontent.com/keshiba/better-minima/master/screenshot.png)

## Installation

Add this line to your Jekyll site's Gemfile:

```ruby
gem "better-minima"
```

And then execute:

    $ bundle

This will fetch the gem and store it locally.

Then, to use this theme, change the `theme` variable in your `_config.yml`
```
theme: "better-minima"
```

### NOTE - Github Pages
If you want to host your Jekyll blog on GitHub, you need to follow the steps given below.


#### Step1 - Add gem
Add the gem `jekyll-remote-theme` to your `Gemfile`.
```
gem "jekyll-remote-theme"
```

#### Step2 - Modify _config.yml
Add the plugin `jekyll-remote-theme` to your plugins list in `_config.yml`
```
plugins:
  - jekyll-remote-theme
```

#### Step3 - Set remote-theme
Add the theme name `keshiba/better-minima` to the `remote-theme` variable.
```
theme: minima
remote-theme: "keshiba/better-minima"
```

#### Step4 - Install gem
Run the `bundle` command to download and install the plugin
```
$ bundle
```

## Usage

### Hero Name
To get your name on the homepage as shown in this preview, add the following block to `_config.yml`
```
author:
  name: imarandomguy
```

### Social Links
To get the social links on your home page as shown in this preview, add the `social_links` block to `better-minima` config in `_config.yml`
```
better-minima:
  social_links:
    twitter: imarandomguy
    github: randomguy
    telegram: randomguy
```

For a list of all social links supported by this theme, take a look at this [_config.yml](https://github.com/keshiba/better-minima/blob/master/_config.yml) file.

### Featured Posts
A list of *Featured Posts* are displayed on the homepage.
To add a post to this list, set the `featured` variable to `true`.

```
---
title: "This is a featured post"
featured: true
---
Post content goes here
```

### Recent Posts
The "Recent Posts" section shows 10 recent posts (by default) in it. 
To change the recent posts count, add the following property to `_config.yml`.

```
recent_posts_count: 15
```

### Pagination

Unlike minima, better-minima shows just the *Featured Posts* and *Recent Posts* on the homepage. 
The "All Posts" section must be on a separate page for pagination to work correctly.

To enable pagination, follow the steps given below.


#### Step 1 

To `_config.yml`, add the following properties
```
paginate: 5
paginate_root_path: "/blog/"
paginate_path: "/blog/page:num/
```
`paginate:5` - This enables pagination and instructs the theme to show *5* posts in a page.

`paginate_root_path: "/blog/"` - This is your preferred URL path to navigate to the "All Posts" section.

`paginate_path: "/blog/page:num/` - This is the path used by Minima to navigate to other pages while paginating. `:num` is the placeholder for page number.

#### Step 2
To `_config.yml`, add the plugin `jekyll-plugins` to the `plugins` block

```
plugins:
 - jekyll-paginate
```

#### Step 3
Add gem dependency to `Gemfile`

```
gem 'jekyll-paginate', '>= 1.1.0
```

#### Step 4

Create a new folder in your project's base directory with the name which you provided for `paginate_root_path` in `_config.yml`

For example, if your jekyll site is located at `D:\Sites\MySite`, then you should create the folder at `D:\Sites\MySite\blog\`


#### Step 5

Download [index.html](https://github.com/keshiba/better-minima/blob/master/blog/index.html) into the folder which you created in Step-2.

This file will serve as the template for pagination and must be included exactly in the `paginate_root_path`.


## For More Information

Visit https://github.com/jekyll/minima


## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/keshiba/better-minima. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.


## License

The theme is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).
