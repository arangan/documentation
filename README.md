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

### Modifications inside `_config.yml`

Set the following values as mentioned below

- baseurl: "/documentation"
- url: "https://arangan.github.io"

### Convert to a regular theme

Comment the `theme: minima` line from `_config.yml`  
Comment the `gem "minima", "~> 2.0` line from `Gemfile`  
Copy all the directories under the Theme to the Jekyll project folder  
Eg. For the minima theme.. copy the following directories

```text
_includes  
_layouts  
_sass  
assets  
```

Execute `bundle update`

Made necessary changes to the theme inside the `_layouts` directory.
