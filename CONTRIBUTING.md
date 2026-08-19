# Contributing to Flowbite React

First off, thank you for considering contributing to Flowbite React. It's people like you that make it a great library for everyone.

Following these guidelines helps to communicate that you respect the time of the developers managing and developing this open source project. In return, they should reciprocate that respect in addressing your issue, assessing changes, and helping you finalize your pull requests.

## Table of Contents

- [Your First Code Contribution](#your-first-code-contribution)
- [Improving The Documentation](#improving-the-documentation)
- [Commit Message Format](#commit-message-format)
- [Pull Request Process](#pull-request-process)
- [Styleguides](#styleguides)
  - [Code Style](#code-style)
  - [Testing](#testing)
  - [Changesets](#changesets)

## Your First Code Contribution

### Requirements

- [Bun](https://bun.sh/) (the repo pins `bun@1.3.8` via the `packageManager` field in `package.json`)
- [Node.js](https://nodejs.org/) (used by the Changesets release tooling)

### Environment Setup and Development

1. Fork the repository and clone your fork:

   ```
   git clone https://github.com/<your-username>/flowbite-react.git
   cd flowbite-react
   ```

2. Install dependencies:

   ```
   bun install
   ```

3. Start the development environment (Storybook and the docs site):

   ```
   bun dev
   ```

4. Run the checks before opening a pull request:

   ```
   bun test
   bun lint
   bun typecheck
   bun format:check
   ```

### Finding an Issue to Work On

Look for issues labeled [`good first issue`](https://github.com/themesberg/flowbite-react/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22) or [`help wanted`](https://github.com/themesberg/flowbite-react/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22). Comment on the issue to let maintainers know you are working on it.

## Improving The Documentation

The documentation site lives in the `apps/web` workspace of this repository. Improvements to component docs, guides, and examples are welcome. Run `bun dev:web` to preview the docs site locally.

## Commit Message Format

This repository uses [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>
```

- `type`: `feat`, `fix`, `docs`, `test`, `refactor`, `perf`, `chore`, `build`, `ci`, `style`
- `scope`: the package or component the change affects, e.g. `cli`, `docs`, `Modal`, `Button`

Examples from the repository history:

- `fix(cli): update bin path to use relative path`
- `fix(docs): accordion light/dark images to render in Safari`
- `feat(Modal): add dismissible prop`

## Pull Request Process

1. Create a branch with a descriptive name, e.g. `fix/modal-close-button`.
2. Make your changes and commit them with a Conventional Commits message.
3. Run `bun test`, `bun lint`, `bun typecheck`, and `bun format:check` and make sure everything passes.
4. If your change affects the published package's behavior or public API, add a changeset:

   ```
   bun changeset add
   ```

   Test-only and docs-only changes do not need a changeset.
5. Open a pull request against `main` and fill out the pull request template.

## Styleguides

### Code Style

- The repo uses [ESLint](https://eslint.org/) and [Prettier](https://prettier.io/) via turbo. Run `bun lint:fix` and `bun format` before committing.
- Components live in `packages/ui/src/components/<ComponentName>/` with a sibling `<ComponentName>.test.tsx` test file.

### Testing

- Tests use [Vitest](https://vitest.dev/) and [React Testing Library](https://testing-library.com/react). Run the full suite with `bun test` or `bun test:coverage`.
- New components must ship with tests covering rendering, class name merging, ref forwarding, and theme overrides, mirroring the sibling component tests.

### Changesets

- User-facing changes to the published package require a [Changesets](https://github.com/changesets/changesets) entry. Run `bun changeset add`, pick a bump level, and describe the change.
- Maintainers run `bun changeset version` and `bun release` to version and publish from `main`.
