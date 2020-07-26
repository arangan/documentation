# Documentation

This project used the github pages to publish a few quick reference manuals.

## Using Jekyll

Inside the folder where you want to init a new Jekyll project.

- `jekyll new .`
- `bundle exec jekyll serve --livereload`

## To publish to github

### Modifications inside `Gemfile`

- Comment the line `gem "jekyll", "~> 3.8.7"`
- Un-Comment the line `gem "github-pages", group: :jekyll_plugins`
- `bundle install`
- `bundle update`
- `bundle install`

### Modifications inside `_config_yml`

Set the following values as mentioned below

- baseurl: "/documentation"
- url: "https://arangan.github.io"
