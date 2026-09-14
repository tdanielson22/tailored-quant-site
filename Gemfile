source "https://rubygems.org"

# GitHub Pages' supported Jekyll + plugin versions.
# Using this gem (rather than a bare `gem "jekyll"`) keeps you
# compatible with what GitHub actually builds on their servers.
gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-remote-theme"
  gem "jekyll-feed"
  gem "jekyll-sitemap"
  gem "jekyll-seo-tag"
  gem "jekyll-include-cache"
end

# Windows/JRuby specific gems, harmless to leave in
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
