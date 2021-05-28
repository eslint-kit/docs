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

### ESLint couldn't determine the plugin "foo" uniquely

It happens when some of your packages depend on the same plugin.

Most often, it comes from CRA's `react-scripts` or Gatsby.

I recommend you to use Yarn. It has some good features to help us with this issue.

Let's assume the problematic plugin is `eslint-plugin-import`.

Use the following command:

```bash
$ yarn why eslint-plugin-import
```

You'll see something like:

```text
=> Found "eslint-plugin-import@2.22.1"
info Has been hoisted to "eslint-plugin-import"
info Reasons this module exists
   - Specified in "devDependencies"
   - Hoisted from "gatsby#eslint-plugin-import"
=> Found "@eslint-kit/eslint-config-base#eslint-plugin-import@2.22.1"
info This module exists because "razzle" depends on it.
info Disk size without dependencies: "944KB"
info Disk size with unique dependencies: "11.91MB"
info Disk size with transitive dependencies: "12.97MB"
info Number of shared dependencies: 43
```

In that case, the problem is Gatsby. And as you see in the second `=> Found` line, `@eslint-kit` currently uses `2.22.1` version of `eslint-plugin-import` \(this is just an example - use the version from your output\).

With the information above, we can fix the issue using yarn `resolutions`. Add the following in your `package.json`:

{% code title="package.json" %}
```text
"resolutions": {
  "gatsby/eslint-plugin-import": "2.22.1"
}
```
{% endcode %}

