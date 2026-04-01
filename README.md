# Sonauto Blog

This folder is a minimal Jekyll blog designed to publish directly on GitHub Pages.

## Writing posts

Add a markdown file to `_posts/` using this format:

```md
---
layout: post
title: "Your Post Title"
date: 2026-04-01
author: Your Name
role: Optional Role
---

Write the post in Markdown here.
```

Use the filename format `YYYY-MM-DD-your-slug.md`.

## Publishing

Push to the default branch for the GitHub Pages repository. GitHub Pages will run Jekyll automatically.

## Local preview

If you want local preview later, the standard path is:

```bash
bundle exec jekyll serve
```

That requires Jekyll to be installed locally.
