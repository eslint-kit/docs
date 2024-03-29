# Contributing

## Documentation

The documentation is linked to [eslint-kit/docs](https://github.com/eslint-kit/docs) repo.

Steps to contribute:

* Fork the repo.
* _(optional)_ Checkout to a new branch.
* Make changes, commit them.
* `git push` to your fork.
* Create a pull request into the main repo.

## CLI / Presets

Everything is located in [eslint-kit/eslint-config-kit](https://github.com/eslint-kit/eslint-config-kit) monorepo.

Steps to contribute:

* Fork the repo.
* _(optional)_ Checkout to a new branch.
* Make changes, cover them with tests (if possible), commit them (any number of times).
* Run `yarn changeset`.\
  Select the affected packages and their bump type.\
  Enter a description for the changelog.\
  Commit the newly added files.\
  _(if you are not sure about the affected packages and their bump type - skip this step)_
* `git push` to your fork.
* Create a pull request into the main monorepo.
