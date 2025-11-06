# React Native Base — AI-assistant-friendly Starter

This repository is a minimal, TypeScript-first React Native starter template intended to be used as a base for building apps quickly with the help of AI code assistants (LLM copilots). The goal is to provide a small, consistent scaffold so you can iterate fast and avoid spending tokens repeatedly asking an LLM to recreate basic project setup.

Why this repository exists

- Save tokens: reduce the amount of prompt context you need to send to an LLM by keeping a compact, well-documented codebase to reference.
- Speed: get a predictable project layout and small set of utilities so code assistants can produce focused changes (features, screens, components) instead of redoing setup.
- Consistency: TypeScript, simple auth context, example API hooks and a few components so new developers and assistants have a stable starting point.

This is intentionally minimal — it gives you the essentials and lets you extend with tools and libraries you prefer.

## What you'll find

- TypeScript React Native project with iOS and Android folders
- Small, predictable folder layout: `src/api`, `src/components`, `src/context`, `src/screens`
- Small example pieces to reuse in LLM prompts:
	- `src/context/AuthContext.tsx` — basic auth scaffold
	- `src/api/driverApi.ts` — example API client
	- `src/screens/home/HomeScreen.tsx` — example screen that ties components together
	- `__tests__/App.test.tsx` — Jest test example

## Quick start (macOS / zsh)

Prerequisites: Node.js, Yarn/npm, Xcode for iOS (if building), Android SDK for Android builds.

Install dependencies and run:

```zsh
npm install
# or
yarn install

cd ios && pod install && cd ..   # macOS only

npx react-native start
npx react-native run-ios   # or
npx react-native run-android
```

Run tests:

```zsh
npm test
# or
yarn test
```

## How this helps when using AI code assistants

When you use an LLM to implement new features, two things waste tokens:

1. Re-describing the project structure and setup in every prompt
2. Asking the assistant to create boilerplate that could be copied from a stable base

This repository mitigates both by providing a compact, documented base the assistant can inspect (or reference) so prompts can focus on the actual feature:

- Instead of "create a React Native app with auth, tests and a products screen", you can prompt the assistant: "Using this repo, add a product detail screen that fetches from /products/:id and reuse existing `Header` and `AuthContext`. Keep changes within `src/screens` and `src/components`."

Recommended prompt pattern

Use small, precise prompts that reference files and responsibilities. Example:

```
Repo: React Native Base (TypeScript). Modify files only under `src/screens/products` and `src/components`. Add a ProductDetail screen that:
- Uses `src/api/driverApi.ts` to fetch product data from /products/:id
- Reuses `Header` component for navigation
- Adds a unit test under `__tests__` that verifies rendering of a product title

Return only modified file diffs or the file contents to be created.
```

This focused style reduces prompt length and tokens because the assistant doesn't need to recreate base setup.

## Project layout (essentials)

- `App.tsx` — app entrypoint
- `index.js` — RN entry
- `src/api/driverApi.ts` — small API helper to centralize network calls
- `src/context/AuthContext.tsx` — basic auth provider pattern
- `src/components/*` — small UI components
- `src/screens/*` — screens and navigation examples
- `__tests__/` — jest tests

## Best practices when pairing with an LLM

- Keep prompts scoped to specific files or folders and reference existing symbols by path.
- Ask the assistant to return diffs or only the changed file contents — this makes applying patches straightforward.
- Provide expected inputs/outputs and small test cases in your prompt so the assistant can produce verifiable code.
- For stateful or backend concerns, prefer to implement or simulate a small mock API rather than sharing real secrets.


