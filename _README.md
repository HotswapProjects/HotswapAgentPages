## Jekyll Documentation theme

Build the site to see the instructions for using it. Or just go here: [http://idratherbewriting.com/documentation-theme-jekyll/](http://idratherbewriting.com/documentation-theme-jekyll/)

## Running the site locally

GitHub Pages builds the site from the `gh-pages` branch with its own versions of Jekyll and plugins
(see [pages.github.com/versions](https://pages.github.com/versions/)). To preview it locally with the same versions,
install Ruby and Bundler and run from your working dir:

```
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. `Gemfile.lock` is not committed, `bundle install` resolves the current `github-pages` gem.
