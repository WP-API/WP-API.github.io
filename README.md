# WP REST API Documentation Site

This repository is the source for [wp-api.org][gh-1]. It powers documentation for the 
[JSON REST API (WP-API)][gh-2] plugin. We are working on making this documentation 
the [best in the world][gh-3], but we're not there yet!

**[Read the Docs ☞][gh-1]**

[gh-1]: http://wp-api.org
[gh-2]: https://github.com/WP-API/WP-API
[gh-3]: https://github.com/WP-API/WP-API.github.io/issues/1


## Running Locally

This site is hosted on Github pages and powered by Jekyll.

  ```bash
    bundle install
    bundle exec jekyll serve -w
  ```

then visit `localhost:4000` in your favorite browser. You can learn more about
using Jekyll and Github pages from their [documentation](https://help.github.com/articles/using-jekyll-with-pages/).

### Using Vagrant

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


## Style Guide

This guide is a limited implementation of [Carwin's Markdown Style Guidelines](https://github.com/carwin/markdown-styleguide).

- Wrap all lines at 80 characters.  
- Denote **bold** text using the asterisk format: `**bold text**`.
- Denote _italic_ text using the underscore format: `_emphasized text_`.
- Force a linebreak by ending a line with two spaces, no more.
- Header text must use the `atx-style` with no closing `#` character.
- Include a space between the `#` and the text of the Header.
- List item lines exceeding 80 characters should, when wrapped, align
  vertically with the beginning of the preceding line's text.  
- **Inline code** must use single backticks and must not have spaces between
  the backtick characters and the code.
- **Fenced code blocks** must be preceded and followed by a newline.
- When used inside _list items_, **fenced code blocks** must be indented as if
  they were one level deeper that the list item that contains them.

