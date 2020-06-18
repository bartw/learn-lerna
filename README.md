# learn lerna

## resources

- https://github.com/lerna/lerna

## getting started

```shell
mkdir learn-lerna
cd learn-lerna
npx lerna init
```

## my first package

```shell
cd packages
npx create-react-app conversations
rm -rf conversations/node_modules
cd ..
npx lerna bootstrap --hoist
cd packages/conversations
npm start
```

## my second package

```shell
cd packages
npx create-react-app settings
rm -rf settings/node_modules
cd ..
npx lerna bootstrap --hoist
cd packages/settings
npm start
```

## so far so good

```shell
npx lerna ls -la
```

## my shared package

```shell
mkdir packages/shared
cd packages/shared
npm init -y
npm install react --save
npm install --save-dev rollup @rollup/plugin-babel babel-preset-es2015-rollup @babel/preset-env @babel/preset-react
```

`.babelrc`

```
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

`rollup.config.js`

```js
import babel from '@rollup/plugin-babel';

const config = {
  input: 'src/index.js',
  output: {
    file: 'lib/index.js',
    format: 'cjs'
  },
  plugins: [babel({ babelHelpers: 'bundled' })]
};

export default config;
```

`package.json`

```json
"scripts": {
  "build": "rollup -c"
}
```

`index.js`

```js
import React from 'react';

const Badge = () => <div>Badge!</div>;

export default Badge;
```

```shell
npm run build
cd ../..
npx lerna bootstrap --hoist
```