# Open Platform Documentation

## Overview

This repository contains the public-facing documentation for 9Spokes data schemas and any future Open Platform documentation.

The content of the `source/` directory are processed by [Slate Docs](https://github.com/slatedocs/slate) which produces static HTML assets under the `build/` directory.

## Manual Method

### Requirements

- Ruby >= 2.3
- NodeJs
- Bundler

### Run

  ```sh
  gem update --system
  gem install bundler
  ```

### Building the project

run:

```sh
bundle install
```

### Running the Development Server

run:

```sh
bundle exec middleman server
```

## Using Docker

Run the Ruby docker image:

```sh
docker run -ti -p 4567:4567  -v `pwd`:/app ruby:2.7 /bin/bash
```

Inside the Docker image, run:

```sh
$ apt update && apt install nodejs -y
$ cd /app
$ bundle config set --local path 'vendor/bundle'
$ bundle install
$ bundle exec middleman server
```

Run by opening your browser to `http://localhost:4567/`
