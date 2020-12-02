# Open Platform Documentation

This repository contains the public-facing documentation for 9Spokes data schemas and any future Open Platform documentation.

The content of the `source/` directory are processed by [Slate Docs](https://github.com/slatedocs/slate) which produces static HTML assets under the `build/` directory.

# Setup

## Required Dependencies 

- Ruby >= 2.3

- NodeJs

- Bundler -  run :

  ```
  gem update --system
  gem install bundler
  ```

## Building the project 

run: 

```
# either run this to run locally
bundle install
```

## Running development server

bundle exec middleman server

