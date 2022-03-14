# Hugo + Stork

This site was built with [Hugo](https://gohugo.io/) and includes the [Stork](https://stork-search.net/) library for full-text search.

This site has 500 articles.

## Building the site locally

```bash
rm -rf public/ static/site.st.json
hugo
./stork build --input public/stork.json --output public/site.st.json
cp public/site.st.json static/site.st.json
hugo server
```

## Related issues and discussions

https://github.com/jameslittle230/stork/discussions/258

https://github.com/jameslittle230/stork/issues/250

https://github.com/jameslittle230/stork/discussions/259
