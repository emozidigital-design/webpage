# CLAUDE.md
## 1. Project overview
- **Project name:** emozitech
- **Type:** Next.js website application
- **Purpose:** Build a fast, scalable, SEO-friendly website with a modern React stack.
- **Target users:**
- **Core features:**
### Current state
- The supplied repo is a frontend-first Next.js project.
- No dedicated backend, database, or auth layer is defined in the provided files.
- Treat this document as the development contract for future work.
## 2. Tech stack
### Frontend
- **Next.js 16.2.2** for routing, rendering, and production builds.
- **React 19.2.4** for UI composition.
- **TypeScript 5** for type safety.
- **Tailwind CSS 4** for utility-first styling.
- **lucide-react** for icons.
- **gsap** for premium motion effects.
### Tooling
- **ESLint 9** with Next.js core-web-vitals and TypeScript presets.
- **PostCSS** with Tailwind’s plugin.
- **npm scripts** for local dev, build, start, and lint.
### Why this stack
- Next.js gives a strong default architecture and rendering model.
- TypeScript reduces runtime bugs and improves refactoring.
- Tailwind accelerates UI delivery and keeps styles consistent.
## 3. Repository structure
### Expected shape
```text
app/
  page.tsx
  globals.css
components/
lib/
public/
```
### Folder roles
- **app/**: routes, layouts, and route-level data logic.
- **components/**: reusable UI sections and widgets.
- **public/**: static assets served directly.
### Placement rules
- Keep route-specific code in `app/`.
- Move reusable UI into `components/`.
- Keep business logic out of JSX when possible.
- Prefer small modules over large files.
## 4. Setup instructions
### Prerequisites
- Node.js LTS.
### Install dependencies
```bash
npm install
```
### Start local development
```bash
npm run dev
```
- Open `http://localhost:3000` in the browser.
### Production build and preview
```bash
npm run build
npm run start
```
- Run `build` before deployment.
- Use `start` to validate the production output locally.
### Lint
```bash
npm run lint
```
- Fix lint errors before merging.
- Do not disable rules without a clear reason.
### Environment variables
- Store secrets in `.env.local`.
- Never commit environment files containing credentials.
- Document required variables in README or an env example file.
## 5. Coding standards
### TypeScript
- Keep strict typing on.
- Use path alias imports when they improve readability.
### React and Next.js
- Prefer server components by default.
- Use client components only for interactive behavior.
### Styling
- Use Tailwind consistently.
- Maintain consistent spacing, typography, and color usage.
### Animation
- Use GSAP only when motion improves the experience.
- Respect reduced-motion preferences.
### Code quality
- Keep components single-purpose.
- Remove dead code quickly.
## 6. API structure
### Current status
- No backend API routes are defined in the supplied files.
- Treat the app as frontend-first unless API work is added later.
### If APIs are introduced
- Use `app/api/<resource>/route.ts`.
- Return predictable JSON shapes.
### Example
```ts
export async function GET() {
  return Response.json({ ok: true });
}
```
## 7. Deployment workflow
### Build flow
1. Pull the latest branch.
2. Install dependencies.
3. Run lint.
4. Build the app.
5. Deploy after a successful build.
### Commands
```bash
npm install
npm run lint
npm run build
npm run start
```
### Hosting
- Vercel is the default fit for this stack.
### CI/CD expectations
- Lint on every pull request.
- Build on every pull request.
## 8. Performance, security, and SEO
### Performance
- Prefer server rendering for content pages.
- Split large features into route-level chunks.
- Keep animations lightweight.
### Security
- Never commit secrets.
- Validate external input.
- Sanitize user-generated content.
- Limit third-party scripts.
### SEO
- Use unique titles and descriptions.
- Keep semantic heading structure.
- Add descriptive alt text.
- Make content crawlable in HTML.
- Use clean URLs and canonical routes.
### Accessibility
- Ensure keyboard support.
- Preserve focus states.
- Maintain contrast.
- Support reduced motion where relevant.
## 9. Maintenance and scaling
### Routine maintenance
- Review dependency updates regularly.
- Watch Next.js, React, Tailwind, and ESLint changes.
- Remove unused packages.
- Keep TypeScript and lint configs current.
### Scaling guidance
- Add feature folders when the codebase grows.
- Extract shared UI into a design system layer.
- Move repeated logic into hooks or services.
- Separate product, marketing, and content concerns when needed.
### New feature checklist
- Define types first.
- Build the UI next.
- Add behavior after the structure is stable.
- Update docs when architecture changes.
### Release discipline
- Keep changes small.
- Make PRs easy to review.
- Record new env vars and deployment steps.
- Preserve backward compatibility for public routes.
## 10. Project-specific notes
- Package scripts: `dev`, `build`, `start`, `lint`.
- ESLint is configured with Next.js and TypeScript presets.
- Tailwind is wired through PostCSS.
- TypeScript path alias `@/*` is enabled.
- `next-env.d.ts` is auto-managed and should not be edited.
## 11. Contributor agreement
- Prefer clarity over abstraction.
- Follow the existing stack unless there is a strong reason to change it.
- Make local testing possible for every change.
- Update this file when tooling or architecture changes.
## 12. Quick commands
```bash
npm install
npm run dev
npm run lint
npm run build
npm run start
```
## 13. Definition of done
- The feature works in development.
- Lint passes.
- Production build passes.
- Accessibility and SEO impact are checked.
- Documentation is updated where needed.
