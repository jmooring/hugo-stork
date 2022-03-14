# Hugo + Stork

This site was built with [Hugo](https://gohugo.io/) and includes the [Stork](https://stork-search.net/) library for full-text search.

This site has 500 articles.

## Building the site locally

```bash
rm -rf public/ static/site.st
hugo
./stork build --input public/stork.json --output public/site.st
cp public/site.st static/site.st 
hugo server
```
