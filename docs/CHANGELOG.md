# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [Unreleased]

### Added
- Initial project setup with Astro and Tailwind CSS
- Blog system with Content Collections
- About page
- Dark mode toggle with system preference detection
- Newsletter subscription form (ConvertKit integration)
- Responsive layout with mobile support
- SEO meta tags and Open Graph support

### Documentation
- Created `docs/PLAN.md` with implementation plan
- Created `docs/ARCHITECTURE.md` with technical decisions
- Created `docs/CHANGELOG.md` (this file)

## Setup Instructions

### ConvertKit Newsletter
1. Create account at https://convertkit.com
2. Create a new Form
3. Copy the form action URL
4. Update `CONVERTKIT_FORM_ACTION` in `src/components/NewsletterForm.astro`

### Netlify Deployment
1. Push to GitHub
2. Connect repo to Netlify
3. Build settings will be auto-detected
4. Add custom domain (optional)

### Customization
- Update name in `src/components/Header.astro` and `Footer.astro`
- Update social links in `Footer.astro`
- Update site URL in `astro.config.mjs`
- Add profile image to `public/images/`
- Edit `src/pages/about.astro` with your bio
