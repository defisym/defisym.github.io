# Irregulars* blog

Install Ruby 3.3 and Bundler, then run:

```sh
bundle install
bundle exec jekyll serve
```

The Gemfile declares Jekyll 3 and the site's plugins explicitly. Avoid adding the
`github-pages` meta-gem: it pulls in unused plugins and pins dependencies such as
`rubyzip` below their security fixes. The Minima theme and the plugins that render
Markdown files without front matter are retained.

To update and verify dependencies:

```sh
bundle update
bundle exec jekyll build
# Install this audit tool separately from the site's runtime bundle.
gem install bundler-audit
bundle-audit check --update
```

Commit both Gemfile and the Bundler-generated Gemfile.lock. Do not replace exact
versions in the lockfile with version ranges. Dependabot checks for updates weekly.
