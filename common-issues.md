# Common issues

### Errors from @rushstack/eslint-patch

Most often happens in monorepos.

Rename your `.eslintrc` to `.eslintrc.js` and move `patch` config in the following way:

{% code title=".eslintrc.js" %}
```javascript
require("@eslint-kit/eslint-config-patch")

module.exports = {
  extends: [
    "@eslint-kit/base",
  ],
  parser: "babel-eslint",
}
```
{% endcode %}

### Errors related to "parserOptions.project"

 Specify your `tsconfig.json` location manually:

{% code title=".eslintrc" %}
```javascript
{
  "extends": [
    "@eslint-kit/patch",
    "@eslint-kit/base",
    "@eslint-kit/typescript"
  ],
  "parser": "@typescript-eslint/parser",
  "parserOptions": {
    "project": ["./tsconfig.json"]
  }
}
```
{% endcode %}

If it doesn't work, try this:

{% code title=".eslintrc.js" %}
```javascript
const path = require('path')

module.exports = {
  extends: [
    '@eslint-kit/patch',
    '@eslint-kit/base',
    '@eslint-kit/typescript',
  ],
  parser: '@typescript-eslint/parser',
  parserOptions: {
    project: [path.resolve(__dirname, './tsconfig.json')]
  },
}
```
{% endcode %}

