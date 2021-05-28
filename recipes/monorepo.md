# Monorepo

Consider the following:

{% tabs %}
{% tab title="Structure" %}
```text
root/
  packages/
    first/
      package.json
    second/
      package.json
  package.json
```
{% endtab %}

{% tab title="root/package.json" %}
```text
{
  "name": "root",
  "workspaces": [
    "packages/*"
  ]
}
```
{% endtab %}

{% tab title="first/package.json" %}
```
{
  "name": "@root/first"
}
```
{% endtab %}

{% tab title="second/package.json" %}
```
{
  "name": "@root/second"
}
```
{% endtab %}
{% endtabs %}

There are three ways of using ESLint:

* Install in the `root`, use the same config everywhere
* Install in the specific package \(`first`, `second`\), use only there
* Install the common config in the `root` and specific configs in `first` and/or `second`

## Installation in root

Just do it like in a single repo:

```bash
$ npx @eslint-kit/cli
```

It will create the config files in the root and install the dependencies using `-W` yarn option.

## Installation in nested package

Specify the package using `-W, --workspace <name>` option:

```bash
$ npx @eslint-kit/cli --workspace @root/first
```

It will create the config files in the nested package and install the dependencies in its `package.json`.

## The third way

You can combine the commands above and create multiple ESLint configurations in your repo.

