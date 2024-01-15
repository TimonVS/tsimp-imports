# tsimp imports bug reproduction

Use Node.js v18.18.2, ts-node breaks with v18.19.0.

## tsimp

Relative imports work fine:

```sh
node --conditions=development --loader=tsimp/loader src/relative-import.ts
```

[Subpath imports](https://nodejs.org/api/packages.html#subpath-imports) using the `"imports"` field in `package.json` fails with `Error [ERR_MODULE_NOT_FOUND]: Cannot find module '/Users/timon.vanspronsen/Code/tsimp-imports/src/utils/math.js'`.

```sh
node --conditions=development --loader=tsimp/loader src/imports.ts
```

## ts-node

Comparison with ts-node, the below command works, but only after an initial build with `npx tsc` (it does use the development version of `math.ts` afterwards):

```sh
node --conditions=development --loader=ts-node/esm src/imports.ts
```