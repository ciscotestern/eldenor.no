# ELDENOR - Astro Personal Site + Blog

A modern, fast personal website with blog functionality, built with Astro. Features Giscus comments powered by GitHub Discussions.

## 🚀 Quick Start

### Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- [Git](https://git-scm.com/)
- A GitHub account

### Local Development

```bash
# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

## 📁 Project Structure

```
eldenor-astro/
├── public/              # Static assets (favicon, images)
├── src/
│   ├── components/      # Reusable components
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── BlogCard.astro
│   │   ├── SkillCard.astro
│   │   └── Giscus.astro
│   ├── content/
│   │   └── blog/        # Blog posts (Markdown/MDX)
│   ├── layouts/
│   │   ├── BaseLayout.astro
│   │   └── BlogPost.astro
│   ├── pages/
│   │   ├── index.astro      # Home page
│   │   ├── about.astro      # About page
│   │   ├── rss.xml.js       # RSS feed
│   │   └── blog/
│   │       ├── index.astro  # Blog listing
│   │       └── [slug].astro # Individual posts
│   └── styles/
│       └── global.css
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

## ✍️ Writing Blog Posts

Create a new `.md` or `.mdx` file in `src/content/blog/`:

```markdown
---
title: "Your Post Title"
description: "A brief description for previews and SEO"
pubDate: 2024-12-28
category: "HomeLab"
tags: ["networking", "automation"]
heroImage: "/images/optional-hero.jpg"
---

Your content here...
```

### Frontmatter Fields

| Field | Required | Description |
|-------|----------|-------------|
| `title` | Yes | Post title |
| `description` | Yes | Short description |
| `pubDate` | Yes | Publication date (YYYY-MM-DD) |
| `category` | No | Category name (default: "Uncategorized") |
| `tags` | No | Array of tags |
| `heroImage` | No | Path to hero image |
| `updatedDate` | No | Last updated date |

## 💬 Setting Up Giscus Comments

1. **Create a GitHub repo** for your site (e.g., `eldenor/eldenor.no`)

2. **Enable Discussions** in your repo:
   - Go to repo Settings → General → Features
   - Check "Discussions"

3. **Configure Giscus** at [giscus.app](https://giscus.app):
   - Enter your repo name
   - Choose "Announcements" category (recommended)
   - Copy the configuration values

4. **Update the Giscus component** in `src/components/Giscus.astro`:

```astro
const {
  repo = "YOUR_USERNAME/YOUR_REPO",        // e.g., "eldenor/eldenor.no"
  repoId = "YOUR_REPO_ID",                 // From giscus.app
  category = "Announcements",
  categoryId = "YOUR_CATEGORY_ID",         // From giscus.app
} = Astro.props;
```

## 🌐 Deployment

### Option 1: Netlify (Recommended)

1. Push your code to GitHub
2. Go to [netlify.com](https://netlify.com) and sign in with GitHub
3. Click "Add new site" → "Import an existing project"
4. Select your repository
5. Build settings are auto-detected:
   - Build command: `npm run build`
   - Publish directory: `dist`
6. Click "Deploy"

**Custom domain:**
- In Netlify: Site settings → Domain management → Add custom domain
- Add DNS records at your registrar (Hostinger):
  ```
  Type: CNAME
  Name: www
  Value: your-site-name.netlify.app
  
  Type: A
  Name: @
  Value: 75.2.60.5 (Netlify's load balancer)
  ```

### Option 2: Vercel

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com) and import your repo
3. Framework preset: Astro (auto-detected)
4. Deploy!

### Option 3: GitHub Pages

Add to `astro.config.mjs`:
```js
export default defineConfig({
  site: 'https://yourusername.github.io',
  base: '/your-repo-name',
  // ... rest of config
});
```

Create `.github/workflows/deploy.yml`:
```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm ci
      - run: npm run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    permissions:
      pages: write
      id-token: write
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/deploy-pages@v4
        id: deployment
```

## 🎨 Customization

### Colors

Edit CSS variables in `src/styles/global.css`:

```css
:root {
  --color-accent: #00d4aa;      /* Main accent color */
  --color-secondary: #7c5cff;   /* Secondary accent */
  --color-bg: #0a0a0f;          /* Background */
  /* ... */
}
```

### Fonts

The site uses:
- **Outfit** - Display/headings
- **JetBrains Mono** - Code and monospace

Change in `global.css` by updating the Google Fonts import.

### Adding Pages

Create a new `.astro` file in `src/pages/`:

```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
---

<BaseLayout title="New Page">
  <section class="container">
    <h1>New Page</h1>
    <p>Content here</p>
  </section>
</BaseLayout>
```

Then add it to the navigation in `src/components/Header.astro`.

## 📝 License

MIT License - feel free to use this template for your own site!

---

Built with ❤️ using [Astro](https://astro.build)
