# Basics

---

TypeScript adds typing to your JavaScript that makes developing easier.
It will still run buggy code, but it will allow your IDE to see the bug before 
you run any code.

---

## Executing TypeScript with Node

You should have the following files:
`tsconfig.json`, `package.json`, `app.ts`, and `server.ts`.

I use `tpx` [library](https://tsx.is/) to execute my TypeScript in Node.

Have this script in your package.json
```shell
    "start": "npx tsx server.ts",
```

## `as const` with literal types

Use `as const` so that TypeScript can 
infer literal types (e.g., "specific string" instead of just string).

For example: 
```typescript
const gameBoardSizes = {
    beginner: { rowNum: 12, colNum: 24 },
    easy: { rowNum: 14, colNum: 26 },
} as const; // Remove this if you want to see more generic 'number'

type tGameBoardSizes = typeof gameBoardSizes; // hover over tGameBoardSizes to see
```

## Making a type for all keys in an object

```typescript
type tGameDifficulty = keyof tGameBoardSizes; // "beginner" | "easy"
```