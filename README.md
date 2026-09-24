# Base Angular Project

A minimal Angular 22 starter with standalone components, routing, SCSS, strict TypeScript checks,
type-aware ESLint, Prettier, and Vitest unit tests. The root component contains a router outlet and
starts with no routes, so a blank page is expected until you add a feature.

## Getting started

Use a Node.js version supported by the installed Angular CLI. This starter has been verified with
Node.js 26.10.0 and declares npm 11.19.1 in `package.json`. A Node version is not currently pinned.

From the project directory:

```sh
npm ci
npm start
```

Open http://localhost:4200/. Changes to source files reload the development application.
Use `npm ci` for an existing checkout to install the versions recorded in `package-lock.json`.
Use `npm install` when deliberately changing dependencies, and commit the updated lockfile.

## Commands

| Command                | Purpose                                                                     |
| ---------------------- | --------------------------------------------------------------------------- |
| `npm start`            | Start the development server.                                               |
| `npm run build`        | Create an optimized production build under `dist/base-angular-project/`.    |
| `npm run watch`        | Rebuild development output when files change.                               |
| `npm test`             | Run unit tests interactively with watch mode.                               |
| `npm run test:ci`      | Run unit tests once without watching.                                       |
| `npm run lint`         | Check TypeScript and Angular templates.                                     |
| `npm run lint:fix`     | Apply available ESLint fixes, including attribute ordering.                 |
| `npm run format`       | Format supported files with Prettier.                                       |
| `npm run format:check` | Check formatting without modifying files.                                   |
| `npm run check`        | Run lint, formatting checks, unit tests, and the production build in order. |

Run `npm run check` before sharing changes. It stops at the first failed command. ESLint warnings
currently do not fail the check. No CI workflow or end-to-end test runner is configured; CI can run
`npm ci` followed by `npm run check`.

## Editor setup

Open the project folder in VS Code and install the workspace's recommended extensions:

- Angular Language Service (`angular.ng-template`)
- ESLint (`dbaeumer.vscode-eslint`)
- Prettier (`esbenp.prettier-vscode`)

Workspace settings make Prettier the default formatter and enable formatting on save. Explicit saves
such as Ctrl+S also apply ESLint fixes to TypeScript and HTML. Non-fixable findings remain visible in
the Problems panel. Prettier handles formatting; Angular ESLint handles attribute ordering.

## Project conventions

- Use standalone components, directives, and pipes. The Angular compiler enforces this convention.
- Keep application code in `src/app/`, routes in `app.routes.ts`, and application providers in `app.config.ts`.
- Group related files by feature as the application grows. Keep component tests beside their source files.
- Generate components with SCSS, for example `npm exec -- ng generate component features/home`.
- Use the `app` selector prefix. Component selectors use kebab-case; attribute directive selectors use camelCase.
- Use modern Angular control flow such as `@if` and `@for`. Template accessibility rules are enabled.
- TypeScript enables strict checking, checked indexed access, and exact optional property types.
- ESLint uses type-aware recommended rules. Additional conventions include explicit function return types,
  omitted `public` modifiers, and a 400-line TypeScript file limit excluding comments and blank lines.
- Prettier uses single quotes and a 120-character print width. Formatting exclusions live in `.prettierignore`.
- Keep the global reset in `src/styles.scss`; put component-specific styling in component SCSS files.

Production builds enforce bundle budgets: the initial bundle warns at 500 kB and fails at 1 MB;
individual component styles warn at 4 kB and fail at 8 kB. Adjust these deliberately in `angular.json`
as the application develops.

## Tests

Tests use Vitest through Angular's unit-test builder with jsdom. Place tests in `*.spec.ts` files.
The starter includes a root-component creation test; add behaviour tests alongside each feature.
Browser interaction and end-to-end testing require a separate setup.

## Reusing the starter

1. Change the package name in `package.json`, then run `npm install --package-lock-only` to update lockfile metadata.
2. Rename the project key under `projects` in `angular.json` and update its development and production
   `buildTarget` references. The default build output directory follows the project name.
3. Change the page title in `src/index.html` and replace `public/favicon.ico`.
4. If changing the `app` prefix, update `angular.json`, both selector rules in `eslint.config.js`, existing
   selectors, the root element in `src/index.html`, and the `app-root` rule in `src/styles.scss`.
5. Add your first route and component, update this README for the application, and run `npm run check`.
