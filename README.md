# Personal website

https://abourdon.github.io

Based on the [end2end Clean Jekyll theme](https://github.com/nandomoreirame/end2end)

## Details

Two main branches:
- `source`, where the site's development sources are contained
- `master`, where the site's generated static files are deployed

When developing:

```bash
$ bundle install
$ bundle exec jekyll serve
```

To create a new post: 

```bash
$ bundle exec rake post title="my beautiful post"
```

To create a new page:

```bash
$ bundle exec rake page name="contact.md"
```

To deploy:

```bash
$ bundle exec rake
```