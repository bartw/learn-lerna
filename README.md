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
cd ../..
npx lerna bootstrap --hoist
cd packages/conversations
npm start
```