# react-new-jsx-transform

## Manual installation

```bash
$ yarn add -D @eslint-kit/eslint-config-react-new-jsx-transform
```

## When to use it?

Use it when you don't need to import React when using JSX.

#### Longer explanation

Check out [this post](https://ru.reactjs.org/blog/2020/09/22/introducing-the-new-jsx-transform.html) in React blog.

{% hint style="info" %}
ESLint Kit CLI automatically detects supported CRA / Next / Gatsby / Babel versions and installs the config.
{% endhint %}

## Rules

```javascript
{
  'react/jsx-uses-react': 'off',
  'react/react-in-jsx-scope': 'off',
}
```

