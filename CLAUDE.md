# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Philosophy

- **Mobile-first, responsive design**: Every component starts at the smallest breakpoint and scales up via media queries or Tailwind breakpoints (`sm`, `md`, `lg`, `xl`, `2xl`).
- **Performance-obsessed**: Target Core Web Vitals >90 on Lighthouse. Lazy load images/routes, compress assets (WebP <100KB), defer non-critical JS, no render-blocking scripts.
- **Accessible by default**: WCAG 2.2 AA compliance — semantic HTML, alt text, keyboard navigation, ARIA roles, sufficient color contrast.
- **SEO-first markup**: Semantic HTML5 elements (`<main>`, `<article>`, `<section>`), meta tags, Open Graph, structured data (JSON-LD), sitemaps.
- **Sustainable code**: Minimize bundle size and network requests. Efficient rendering. No unnecessary dependencies.
- **Distinctive design**: Avoid generic/overused patterns. Aim for premium, intentional aesthetics with bold typography, considered color palettes, and purposeful micro-interactions. Never default to safe/bland choices.

## Tech Stack Defaults

Choose based on project type:
- **Static sites**: HTML/CSS/JS, Tailwind CSS, Vite
- **Dynamic apps**: React 19+ with Next.js 15+ (App Router), TypeScript strict mode
- **Styling**: Tailwind CSS with PostCSS; CSS variables for theming
- **Backend (when needed)**: Node.js/Express or Next.js API routes
- **Testing**: Vitest for unit/integration, Playwright for E2E
- **Linting**: ESLint with strict config, Prettier for formatting
- **Deployment**: Optimized for Vercel/Netlify with CI/CD

## Code Conventions

- Functional components only (React). No class components.
- TypeScript in strict mode for all JS-heavy projects.
- Semantic HTML5 — use the right element, not `<div>` soup.
- CamelCase for JS/TS identifiers, kebab-case for CSS classes.
- Descriptive names: `userProfile` not `up`, `isMenuOpen` not `flag`.
- No file exceeds 300 lines — extract into modules.
- Comments only for complex logic. Use JSDoc for exported functions.
- Imports ordered: external libs, internal modules, styles, types.

## File Structure

```
src/
  components/    # Reusable UI components
  pages/         # Route-level page components
  layouts/       # Page layout wrappers
  hooks/         # Custom React hooks
  lib/           # Utility functions and helpers
  styles/        # Global styles and theme config
  types/         # TypeScript type definitions
  api/           # API route handlers (if applicable)
public/
  assets/        # Static assets (images, fonts, icons)
```

## Guardrails

- **Never** commit API keys or secrets — use `.env` files and environment variables.
- **Never** ignore mobile breakpoints — test every component at 320px, 768px, 1024px, 1440px.
- **Never** use deprecated APIs or libraries with known vulnerabilities.
- **Always** sanitize user inputs. Use HTTPS. Validate on both client and server.
- **Always** handle errors gracefully with user-friendly messages (log details to console in dev, structured logging in prod).
- Avoid deep nesting (>3 levels), magic numbers, and untested code paths.
- Images must use WebP format with explicit `width`/`height` to prevent layout shift.

## Workflow

1. **Plan first**: Outline the approach before writing code. For features, write a brief PRD with user stories and acceptance criteria.
2. **Build in order**: Schema/data model → backend/API → frontend components → integration → tests.
3. **Test before commit**: Run `npm run lint` and `npm run test` before every commit.
4. **Optimize last**: Get it working correctly first, then optimize for performance.

## Build & Dev Commands

```bash
npm run dev          # Start dev server
npm run build        # Production build
npm run lint         # Run ESLint
npm run test         # Run test suite
npm run test -- --run [file]  # Run single test file
```
