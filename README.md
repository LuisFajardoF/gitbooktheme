# Jekyll GitBook

Make Jelly site have a GitBook look!

## Why Jekyll with GitBook

GitBook is an amazing frontend style to present and organize contents (such as book chapters
and blogs) on Web. The typical to deploy GitBook at [Github Pages][1]
is building HTML files locally and then push to Github repository, usually to the `gh-pages`
branch. It's quite annoying to repeat such workload and make it hard for people do version
control via git for when there are generated HTML files to be staged in and out.

This theme takes style definition out of generated GitBook site and provided the template
for Jekyll to rendering markdown documents to HTML, thus the whole site can be deployed
to [Github Pages][1] without generating and uploading HTML bundle every time when there are
changes to the original repo.

## How to Get Started

This theme can be used just as other [Jekyll themes][1].

This repository fork of: [sighingnow][3].

# Compile with Ruby

Change ruby version: 2.5.5 in `Gemfile` _(2.5.5 is a Ruby version of my system)_.

In Terminal:
```
bundle install
bundle exec jekyll serve
```

Or execute the files in folder `scripts`:

```
sh scripts/bootstrap
sh scripts/server
```

The last command open a conection _(localhost)_ in the next address: `http://127.0.0.1:4000/gitbooktheme/` 

## License

This work is open sourced under the Apache License, Version 2.0.

Copyright 2019 Tao He.

[1]: https://pages.github.com
[2]: https://pages.github.com/themes
[3]: https://github.com/sighingnow/jekyll-gitbook/
