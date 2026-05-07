# CLAUDE.md — AAO Data Lab Tool

This repo is an **AAO Data Lab web tool** built with React + Vite + Tailwind CSS. Use this file for task context.

## Repo Layout

```
src/
  components/   # Shared UI components
  features/     # Feature-specific modules
  data/         # Static data, constants, mock fixtures
  hooks/        # Shared React hooks
  utils/        # Pure utility functions
  App.jsx       # Root — includes required AAO components
  main.jsx
index.html            # Loads AAO banner CDN script
tailwind.config.js    # AAO design tokens
.github/workflows/deploy.yml  # GitHub Pages deploy action
```

## Required in Every Build

`App.jsx` must always contain — do not remove:

```jsx
<aao-site-header mode="compact" dev-url="https://lab.allaboardohio.org"></aao-site-header>
<aao-notification
  config-url="https://raw.githubusercontent.com/all-aboard-ohio/aao-lab-components/main/banner.json"
></aao-notification>
```

If using paid cloud infrastructure (Google Cloud), also include `<aao-donation></aao-donation>`.

## Key Constraints

- No personal data collection, no analytics trackers
- WCAG 2.1 AA minimum — test with axe DevTools before every PR
- Use AAO Tailwind token classes (`aao-dark-blue`, `aao-dark-red`, etc.) — never raw hex values
- Mobile-first with Tailwind breakpoints
- Prefer static/client-side over server-side wherever possible

## Task Playbooks

**Adding a component:**
1. Create `src/components/ComponentName.jsx`
2. Use `font-heading` for headings, `font-body` for body text, AAO color tokens
3. Add semantic HTML and ARIA labels for accessibility

**Changing content/data:**
- Static data lives in `src/data/`
- Fetch logic belongs in a custom hook in `src/hooks/`

**Deploying:**
- Push to `main` → GitHub Actions auto-deploys to GitHub Pages
- For a custom subdomain (`*.lab.allaboardohio.org`), request in `#infrastructure` on Slack
- Check `.github/workflows/deploy.yml` for config

## Reference Docs

- Mission & ethos: https://github.com/all-aboard-ohio/aao-lab-docs/blob/main/mission-ethos.md
- Style guide: https://github.com/all-aboard-ohio/aao-lab-docs/blob/main/style-guide.md
- Requirements: https://github.com/all-aboard-ohio/aao-lab-docs/blob/main/requirements.md
- Architecture: https://github.com/all-aboard-ohio/aao-lab-docs/blob/main/architecture.md
- Contributing: https://github.com/all-aboard-ohio/aao-lab-docs/blob/main/contributing.md
- Project management: https://github.com/all-aboard-ohio/aao-lab-docs/blob/main/project-management.md
