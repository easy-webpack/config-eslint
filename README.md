# @easy-webpack/config-eslint
Lint JavaScript files using [eslint](http://eslint.org/) and [eslint-loader](https://github.com/MoOx/eslint-loader).

# Installation
```
npm install --save-dev @easy-webpack/config-eslint
```
[easy-webpack](https://github.com/easy-webpack/core) is also required.

# Usage
```js
// webpack.config.js
const generateConfig = require('@easy-webpack/core').generateConfig;

const baseConfig = { ... }; // project-specific config like the entry file

module.exports = generateConfig(
  baseConfig,

  require('@easy-webpack/config-eslint')
    ({ /* Options object */ fix: true, cache: true }, /* Exclude */ /(node_modules|bower_components)/)
);

// .eslintrc.json
{
  "parserOptions": {
    "ecmaVersion": 2017,
    "sourceType": "module",
    "ecmaFeatures": {
      "jsx": true
    }
  },
  "env": {
    "browser": true,
    "commonjs": true
  },
  "extends": "eslint:recommended"
}

// This config will lint JavaScript files and potentially fix it  
```

# Options
The first parameter will be passed into eslint-loader directly. Read [their documentation](https://github.com/MoOx/eslint-loader#options) for details.

The second parameter is the exclude files matcher. Default: `node_modules`.

Check [webpack documentation](https://webpack.js.org/configuration/module/#condition) on how to write valid exclude files.

# Related tutorials
 - [Configuring eslint](http://eslint.org/docs/user-guide/configuring)

# Tips
## Enable cache
Cache can speed up build performance. This can greatly reduce rebuilt time and enhance productivity.
 
Enable cache by setting `cache` to true in options object.

```js
require('@easy-webpack/config-eslint')
  ({cache: true})
```