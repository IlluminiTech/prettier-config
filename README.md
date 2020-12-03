# prettier-config

This package provides Illumini's base [`prettier`](https://prettier.io) configuration.

Pairs well with our [`ESLint configuration`](https://www.npmjs.com/package/@illumini/eslint-config).

## Table of Contents

- [prettier-config](#prettier-config)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
    - [npm](#npm)
    - [yarn](#yarn)
  - [Configurations](#configurations)
    - [Default Config](#default-config)
  - [Editor Integration & Autoformatting](#editor-integration--autoformatting)
    - [VS Code](#vs-code)
  - [Pre-commit Hook](#pre-commit-hook)
  - [Publishing to npm](#publishing-to-npm)

## Installation

### npm

```sh
npm install --save-dev @illumini/prettier-config
```

If you don't have it installed already, also install `prettier` as a devDependency.

```sh
npm install --save-dev prettier
```

### yarn

```sh
yarn add --dev @illumini/prettier-config prettier
```

## Configurations

We export one ESLint configuration for your usage:

1. [Default](#default-config)

### Default Config

Create a `prettier.config.js` file at the root of your project that contains:

```js
module.exports = require('@illumini/prettier-config');
```

## [Editor Integration & Autoformatting](https://prettier.io/docs/en/editors.html)

### VS Code

1. Install [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) extension: `View → Extensions` then find and install Prettier - Code formatter
2. Reload the editor
3. In your VS Code user settings `Code/File → Preferences → Settings` or `CMD/CTRL + ,` click the `{}` icon in the top right corner to modify your `settings.json` file

   ```json
   // Format on save with Prettier rules
   "editor.formatOnSave": true,
   ```

## Pre-commit Hook

As another line of defence, if you want ESLint to automatically fix your errors on commit, you can use [`lint-staged`](https://github.com/okonet/lint-staged) with [`husky`](https://github.com/typicode/husky), which manages git hooks.

1. `npm install --save-dev lint-staged husky`
2. In your `package.json`:

   ```json
   {
     "lint-staged": {
       "*.js": ["eslint --fix"]
     },
     "husky": {
       "hooks": {
         "pre-commit": "lint-staged"
       }
     }
   }
   ```

## Publishing to npm

Read npm's docs on [How to Update a Package](https://docs.npmjs.com/getting-started/publishing-npm-packages#how-to-update-a-package).

1. `npm login`
   - Make sure you're logged into illumini's npm account with the credentials from 1pass. `npm whoami` will tell you if you're already logged in.
2. `npm version <update_type>`
   - `update_type` can be `patch`, `minor`, or `major`. If you don't know which one to use, go read about [semantic versioning](https://docs.npmjs.com/getting-started/semantic-versioning).
3. `npm publish`
