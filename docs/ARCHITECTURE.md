# Architecture

This document describes the technical architecture and key decisions for the personal site.

## Framework: Astro

We chose [Astro](https://astro.build/) for its:
- **Zero JS by default**: Ships no JavaScript unless needed
- **Content Collections**: Type-safe Markdown handling
- **Component islands**: Add interactivity only where needed
- **Fast builds**: Optimized static site generation

## Styling: Tailwind CSS

[Tailwind CSS](https://tailwindcss.com/) provides:
- **Utility-first**: Rapid styling without leaving HTML
- **Dark mode**: Built-in `dark:` variant support
- **Purging**: Removes unused styles in production
- **Consistency**: Design tokens via configuration

### Dark Mode Implementation

Dark mode uses Tailwind's `class` strategy:

1. `BaseHead.astro` runs an inline script before render to:
   - Check localStorage for saved preference
   - Fall back to system preference (`prefers-color-scheme`)
   - Apply `dark` class to `<html>` element

2. `ThemeToggle.astro` provides a button that:
   - Toggles the `dark` class on `<html>`
   - Persists the choice to localStorage

This prevents flash of incorrect theme on page load.

## Content: Astro Content Collections

Blog posts are managed via Astro's Content Collections:

```
src/content/
└── blog/
    └── my-post.md
```

### Frontmatter Schema

Defined in `src/content/config.ts`:

```typescript
{
  title: string,        // Post title
  description: string,  // SEO description
  pubDate: Date,        // Publication date
  updatedDate?: Date,   // Optional update date
  heroImage?: string,   // Optional hero image
}
```

## Newsletter: ConvertKit

ConvertKit (Kit) is integrated via a simple HTML form with progressive enhancement:

1. Create a form in ConvertKit dashboard
2. Set `PUBLIC_CONVERTKIT_FORM_ACTION` (or edit `src/components/NewsletterForm.astro`)
3. With JS enabled, the form submits in the background and shows an inline success message (no redirect)
4. Without JS, the form falls back to a normal POST + ConvertKit redirect

## Hosting: Netlify

Recommended hosting on [Netlify](https://netlify.com/):

- **Free tier**: Sufficient for personal sites
- **Auto deploys**: Connected to GitHub repo
- **Custom domains**: Free SSL included
- **Build settings**:
  - Build command: `npm run build`
  - Publish directory: `dist/`

## File Organization

```
src/
├── components/     # Reusable UI components
├── layouts/        # Page layouts (wrap pages)
├── pages/          # Routes (file-based routing)
├── content/        # Markdown content
└── styles/         # Global CSS
```

## Key Components

| Component | Purpose |
|-----------|---------|
| `BaseHead.astro` | Meta tags, SEO, theme initialization |
| `BaseLayout.astro` | Page wrapper with header/footer |
| `BlogPostLayout.astro` | Blog post wrapper |
| `Header.astro` | Navigation |
| `Footer.astro` | Footer with social links |
| `ThemeToggle.astro` | Dark mode switch |
| `NewsletterForm.astro` | ConvertKit subscription form |
| `BlogPostCard.astro` | Post preview card |
