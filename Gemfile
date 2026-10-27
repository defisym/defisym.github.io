source "https://rubygems.org"

# Keep the GitHub Pages Jekyll major version, but declare the site's plugins
# explicitly: github-pages also installs unused plugins with vulnerable pins.
gem "jekyll", "~> 4.4"
gem "minima", "~> 2.5"
gem "webrick", "~> 1.9"
gem "kramdown-parser-gfm", "~> 1.1"
gem "kramdown-math-katex", "~> 1.0"
gem "faraday-retry", "~> 2.4", require: "faraday/retry"

group :jekyll_plugins do
  gem "jekyll-gist", "~> 1.5"
  gem "jekyll-octicons"
  gem "jekyll-github-metadata", "~> 2.16"
  gem "jekyll-titles-from-headings", "~> 0.5"
  gem "jekyll-optional-front-matter", "~> 0.3"
  gem "jekyll-default-layout", "~> 0.1"
  gem "jekyll-relative-links", "~> 0.6"
  gem "jekyll-readme-index", "~> 0.3"
end

# Windows and JRuby do not include zoneinfo files.
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", "~> 1.2", ">= 1.2.11"
  gem "tzinfo-data"
end
