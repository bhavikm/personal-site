# Personal Site Plan

## Overview
Build a minimal, clean personal site inspired by Eugene Yan's design with:
- Blog with Markdown posts
- About page with bio
- Email newsletter signup (ConvertKit)
- Dark mode toggle

## Technology Stack

| Component | Choice | Rationale |
|-----------|--------|-----------|
| Framework | **Astro** | Content-focused, fast, great Markdown support |
| Styling | **Tailwind CSS** | Rapid styling, easy dark mode, minimal CSS |
| Newsletter | **ConvertKit** | Free up to 10k subscribers, simple embed form |
| Hosting | **Netlify** | Free tier, automatic deploys from GitHub, custom domain support |

## Project Structure

```
personal-site/
├── docs/                        # Project documentation
│   ├── PLAN.md                  # This implementation plan
│   ├── ARCHITECTURE.md          # Technical architecture decisions
│   └── CHANGELOG.md             # Track changes and updates
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Footer.astro
│   │   ├── NewsletterForm.astro
│   │   ├── ThemeToggle.astro
│   │   ├── BlogPostCard.astro
│   │   └── BaseHead.astro
│   ├── layouts/
│   │   ├── BaseLayout.astro
│   │   └── BlogPostLayout.astro
│   ├── pages/
│   │   ├── index.astro          # Home/Blog listing
│   │   ├── about.astro          # About page
│   │   └── blog/
│   │       └── [...slug].astro  # Dynamic blog post pages
│   ├── content/
│   │   └── blog/                # Markdown blog posts
│   └── styles/
│       └── global.css
├── public/
│   └── images/                  # Static images
├── astro.config.mjs
├── tailwind.config.mjs
├── package.json
└── README.md
```

## Implementation Steps

### 1. Project Setup & Documentation
- Initialize Astro project
- Add Tailwind CSS integration
- Configure Astro for static site generation
- Create `docs/` folder with project documentation

### 2. Base Layout & Components
- Create `BaseLayout.astro` with HTML structure, meta tags
- Build `Header.astro` with navigation (Home, About)
- Build `Footer.astro` with social links

### 3. Dark Mode
- Implement `ThemeToggle.astro` component
- Use Tailwind's `dark:` variants for styling
- Persist theme preference in localStorage
- Respect system preference by default

### 4. Blog System
- Configure Astro Content Collections for type-safe Markdown
- Create `BlogPostLayout.astro` for individual posts
- Build `BlogPostCard.astro` for post previews
- Home page shows recent posts, sorted by date

### 5. About Page
- Simple page with bio content
- Placeholder for profile image

### 6. Newsletter Integration (ConvertKit)
- Create ConvertKit account (free)
- Create a form in ConvertKit dashboard
- Embed form using `NewsletterForm.astro` component
- Style to match site design

### 7. Hosting Setup (Netlify)
- Connect GitHub repo to Netlify
- Configure build command: `npm run build`
- Publish directory: `dist/`
- Optional: Add custom domain

## Design Notes

Following Eugene Yan's minimal aesthetic:
- Clean typography (system fonts or Inter)
- Generous whitespace
- Simple navigation
- Focus on content readability
- Subtle color accents for links/interactive elements
