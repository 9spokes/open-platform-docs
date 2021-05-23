# Open Platform Documentation

## Overview

This repository contains the public-facing documentation for 9Spokes data schemas and any future Open Platform documentation.

The content of the `source/` directory are processed by [Slate Docs](https://github.com/slatedocs/slate) which produces static HTML assets under the `build/` directory.

## Requirements

- Ruby >= 2.3
- NodeJs
- Bundler

## Run

  ```sh
  gem update --system
  gem install bundler
  ```

## Building the project

run:

```sh
bundle install
```

## Running the Development Server

run:

```sh
bundle exec middleman server
```

