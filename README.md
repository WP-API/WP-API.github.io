# WP REST API Documentation Site
This repository is the source for
[WP REST API documentation](http://wp-api.github.io). We're working on making this
documentation [the best in the world][gh-1], but we're not there yet!

[gh-1]: https://github.com/WP-API/WP-API.github.io/issues/1

## Running locally

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
