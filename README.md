# How it works

ESLint Kit consists of many ESLint presets. They are designed to work with each other without any conflicts. In most cases you only need to specify `extends` and `parser` fields. ESLint Kit will take care of composing it.

There are two basic presets - `patch` and `base`.

Almost every ESLint Kit preset has some plugins in its dependencies and uses them from there. Default ESLint module resolution behavior doesn't allow doing it this way. The `patch` preset fixes this problem. It uses [@rushstack/eslint-patch](https://github.com/microsoft/rushstack/tree/master/stack/eslint-patch) under the hood.

The `base` preset encapsulates some base plugins and rules. It is required for using other ESLint Kit presets.

The other presets is optional, select them depending on your goals and project stack.

For example, the config for React + TypeScript project:

{% code title=".eslintrc" %}
```javascript
{
  "extends": [
    "@eslint-kit/patch",
    "@eslint-kit/base",
    "@eslint-kit/typescript",
    "@eslint-kit/react",
    "@eslint-kit/prettier"
  ],
  "parser": "@typescript-eslint/parser"
}
```
{% endcode %}

It requires the following dependencies:

* `eslint` 
* `prettier`
* `@typescript-eslint/parser` 
* `@eslint-kit/eslint-config-patch`
* `@eslint-kit/eslint-config-base` 
* `@eslint-kit/eslint-config-prettier` 
* `@eslint-kit/eslint-config-react` 
* `@eslint-kit/eslint-config-typescript`

