source "https://rubygems.org"

# GitHub Pages 가 자동으로 빌드해주므로 보통 직접 빌드할 일은 없지만,
# 로컬에서 미리보기를 하고 싶다면 `bundle install` 후 `bundle exec jekyll serve` 로 실행하세요.

gem "github-pages", group: :jekyll_plugins
gem "jekyll-remote-theme"
gem "jekyll-seo-tag"
gem "jekyll-sitemap"

# Windows / JRuby 에서 필요한 의존성
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]
