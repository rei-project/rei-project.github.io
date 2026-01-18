# REI Landing Page

Landing page for **REI (Redesigning Execution for Intelligence)** - a concatenative programming framework for AI-first development.

Live at: [rei-project.github.io](https://rei-project.github.io)

## About REI

REI reimagines programming as collaboration between humans, AI, and machines. Using a concatenative, stack-based approach, it creates predictable execution that both humans and AI can reason about effectively.

Part of [Lemon Slice Labs](https://labs.lemonslice.de) - Exploring AI-First Development.

## Development

This is a static site built with [Astro](https://astro.build) using **Bun** as the package manager.

### Commands

| Command | Action |
| :------ | :----- |
| `bun install` | Install dependencies |
| `bun run dev` | Start dev server at `localhost:4321` |
| `bun run build` | Build for production to `./dist/` |
| `bun run preview` | Preview production build locally |

### Project Structure

```
src/
├── assets/          # Images, fonts (processed by Astro)
├── components/      # Astro components for each section
├── layouts/         # Page layout wrapper
├── pages/           # Route pages (index.astro)
└── styles/          # Global CSS and design system
```

## Deployment

Pushes to `main` trigger GitHub Actions to build and deploy to GitHub Pages.

## Related Repositories

- [REI](https://github.com/rei-project/REI) - Main project repository
- [REIVM](https://github.com/rei-project/REIVM) - Core virtual machine
