# Build a Blockchain Startup

## Decentralized Application (dApp) Development and Entrepreneurship

Spring 2022
INDENG 190E-002/290-002
UC Berkeley SCET

Based on the [Material Jekyll Theme](https://github.com/alexcarpenter/material-jekyll-theme)

## Install

https://jekyllrb.com/docs/

### Ubuntu

https://www.ruby-lang.org/en/documentation/installation/#apt

```bash
sudo apt-get install ruby-full
sudo gem update --system
```

> https://github.com/rubygems/rubygems/issues/3269#issuecomment-761600508
> You can ignore that ruby & gems are not the latest release.

```bash
sudo gem install jekyll bundler
```

## Develop

```bash
# From this site's working directory:
bundle install
bundle exec jekyll serve
```

Browse to <http://localhost:4000> -- reload the page after a few seconds to check after file changes.

## Deploy to gh-pages

```bash
# From this site's working directory:
JEKYLL_ENV=production bundle exec jekyll build --destination ./docs
# make a PR that have the `_site` files updated, they automatically get published once merged in to `main`
```
