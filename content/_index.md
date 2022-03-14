+++
date = 2022-03-13T20:36:19-07:00
draft = false
description = 'A Hugo site to test the Stork library for full-text search'
+++
<!-- markdownlint-disable MD041 -->

This site is built with [Hugo](https://gohugo.io/) and includes the [Stork](https://stork-search.net/) library for full-text search. The site contains 500 articles with an average of 520 words per article.

One of the configuration options for Stork is `save_nearest_html_id`.

> If `true`, correlates each word in an HTML document with the nearest ID in the document. The Stork web interface will link directly to that ID, helping your users jump directly to the content they search for.

Test by searching this site for "Hugo" (case-insensitive). It will bring you to Article 042, targeting the heading nearest to the word.

---
