# eldenor.no

My personal website and blog. Built with Astro, hosted on Netlify, comments powered by Giscus.

## What is this?

Just a simple site where I write about homelab stuff, networking, and whatever else I find interesting. No WordPress, no database, no nonsense.

## How it works

1. Write a blog post in Markdown
2. Push to GitHub
3. Netlify auto-builds and deploys
4. Done

No FTP, no manual uploads. Just write and push.

## Local development

```bash
npm install
npm run dev
```

Then open `http://localhost:4321`

## Writing a new post

Create a new `.md` file in `src/content/blog/`:

```markdown
---
title: "Your Post Title"
description: "A short description"
pubDate: 2026-05-03
category: "HomeLab"
tags: ["networking", "homelab"]
---

Your content here...
```

Push to GitHub and it is live in 30 seconds.

## License

Do whatever you want with it. If you find it useful, cool.
