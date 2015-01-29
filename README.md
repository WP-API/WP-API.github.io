# WP REST API Documentation Site

This repository is the source for [wp-api.org][gh-1]. It powers documentation for the 
[JSON REST API (WP-API)][gh-2] plugin. We are working on making this documentation 
the [best in the world][gh-3], but we're not there yet!

**[Read the Docs ☞][gh-1]**

[gh-1]: http://wp-api.org
[gh-2]: https://github.com/WP-API/WP-API
[gh-3]: https://github.com/WP-API/WP-API.github.io/issues/1


We recommend using Vagrant. Here's how you do that:

```bash
$ vagrant up
$ vagrant ssh

# Following commands are now executed on the box
# These install everything you need
$ cd /vagrant
$ sudo apt-get update
$ sudo apt-get install ruby1.9.3 rubygems make
$ sudo gem install bundler
$ bundle install

# To run the site:
$ jekyll serve
```
