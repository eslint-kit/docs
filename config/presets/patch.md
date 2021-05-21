# patch

## Manual installation

```bash
$ yarn add -D @eslint-kit/eslint-config-patch
```

## When to use?

Always use this preset, until you have any problems with it.

#### Long explanation

Almost every ESLint Kit preset has some plugins in its dependencies and uses them from there. Default ESLint module resolution behavior doesn't allow doing it this way. The `patch` preset fixes this problem. It uses [@rushstack/eslint-patch](https://github.com/microsoft/rushstack/tree/master/stack/eslint-patch) under the hood.

Sometimes, you may face the problems with `patch` preset. Usually, it happens in monorepos. Most likely you can find a solution in the [Common issues](../../common-issues.md) section.

