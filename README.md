# Hugo + Stork

This site is built with [Hugo](https://gohugo.io/) and includes the [Stork](https://stork-search.net/) library for full-text search. The site contains 500 articles with an average of 520 words per article.

## Live test sites

- Hosted by GitHub: <https://jmooring.github.io/hugo-stork/>
- Hosted by Netlify: <https://hugo-stork.netlify.app>

## Test locally on Ubuntu

```bash
./build.sh
hugo server --renderToDisk
```

## Notes

Stork generates a binary index file. With this test site, the index file is 6&nbsp;MB. To force hosts such as GitHub Pages or Netlify to compress the file, we give it a `json` extension. We could use `html` or `css` instead, but `json` seemed like a better fit.

GitHub pages uses gzip compression, producing a 2.3&nbsp;MB index file.

Netlify used Brotli compression, though not aggressively, producing a 2.1&nbsp;MB index file.

If you have a host that can serve pre-compressed assets, aggressive Brotli compression produces a 1.5&nbsp;MB file.

## Related issues and discussions

- [Any tips for decreasing index file size?](https://github.com/jameslittle230/stork/discussions/258)
- [Use stopword lists to reduce index size and improve search results](https://github.com/jameslittle230/stork/issues/250)
- [Search metrics](https://github.com/jameslittle230/stork/discussions/259)
- [Compensate for border radius when displaying progress bar](https://github.com/jameslittle230/stork/issues/260)
