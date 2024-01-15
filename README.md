# tsimp imports bug reproduction

Relative imports work fine:

```sh
node --conditions=development --import=tsimp/import src/relative-import.ts
```

[Subpath imports](https://nodejs.org/api/packages.html#subpath-imports) using the `"imports"` field in `package.json` fails with `Error [ERR_MODULE_NOT_FOUND]: Cannot find module '/Users/timon.vanspronsen/Code/tsimp-imports/src/utils/math.js'`.

```sh
node --conditions=development --import=tsimp/import src/imports.ts
```