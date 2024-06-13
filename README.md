# Hugo + Stork

## Upstream project discontinued

The [upstream project](https://github.com/jameslittle230/stork) was discontinued on 18 June 2023 ([see announcement](https://github.com/jameslittle230/stork/discussions/360)).

Switch to [Pagefind](https://pagefind.app/) by [Cloud Cannon](https://cloudcannon.com/):

- Simple to add to an existing site
- Fast indexing and search
- Easy to configure and style

And the project is [well-maintained](https://github.com/cloudcannon/pagefind) by a great team and trusted organization.

## Overview

This site is built with [Hugo](https://gohugo.io/) and includes the [Stork](https://stork-search.net/) library for full-text search. The site contains 500 articles with an average of 520 words per article.

## Test locally on Ubuntu

```bash
./build.sh
hugo server --renderToDisk
```

## Notes

Stork generates a binary index file. With this test site, the index file is 6&nbsp;MB. To force hosts such as GitHub Pages or Netlify to compress the file, we give it a `json` extension. We could use `html` or `css` instead, but `json` seemed like a better fit.

GitHub pages uses gzip compression, producing a 2.0&nbsp;MB index file.

Netlify uses Brotli compression, though not aggressively, producing a 1.8&nbsp;MB index file.

If you have a host that can serve pre-compressed assets, aggressive Brotli compression produces a 1.5&nbsp;MB file.

## Bag of bytes

When examining the page load, you can see that the browser downloads some of the assets in parallel. I ran some experiments, using a large image, to see if there would be any benefit to splitting the Stork index into pieces.

Spoiler alert: splitting the image into chunks does _not_ improve performance.

<https://hugo-stork.netlify.app/tests/>

Large image:

- A single image
- 5,736,890 bytes
- 4032x2268

Large image (2 chunks):

- The same image, split into 2 chunks
- 6,002,033 bytes total
- Each chunk (tile) is 4032x1134

Large image (9 chunks):

- The same image, split into 9 chunks
- 6,045,716 bytes total
- Each chunk (tile) is 1344x756

This is an imperfect test because I am not splitting a binary file. I am creating multiple independent images, so the total size increases due to compression inefficiency. Even though splitting increases total size by only 5 percent, I am seeing a 10 to 20 percent drop in performance.

From these rudimentary tests it appears that splitting the index would not improve performance.

## Related issues and discussions

- [Any tips for decreasing index file size?](https://github.com/jameslittle230/stork/discussions/258)
- [Use stopword lists to reduce index size and improve search results](https://github.com/jameslittle230/stork/issues/250)
- [Search metrics](https://github.com/jameslittle230/stork/discussions/259)
- [Serving pre-compressed Brotli files](https://answers.netlify.com/t/serving-pre-compressed-brotli-files/53515)
