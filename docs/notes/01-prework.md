# Some solutions to fix problem of official scaffold

## Let JS files support import format

### Theory

`nodemon` works with `babel` 

### Implement

1. Edit `package.json`

```json
"scripts": {
    "dev": "cross-env NODE_ENV=development nodemon server/index.js --watch server --exec babel-node",
    "start": "cross-env NODE_ENV=production node server/index.js --exec babel-node",
  },
```

2. config `babel`
new a file named `.babelrc` as project root

```
{
    "presets": ["es2015"]
}
```

3. install dependencies

```shell
yarn add babel-cli babel-preset-es2015 --dev
```

## support sass

```shell
yarn add sass-loader node-scass --dev
```

## unmet peer dependency

For example, `warning " > element-ui@2.13.0" has unmet peer dependency "vue@^2.5.17"`.
`yarn add vue@^2.5.17`


## Add commitizen

install dependencies
```shell
yarn add -D commitizen conventional-changelog cz-conventional-changelog
```

config in `package.json`
```
{
    "config": {
        "commitizen": {
          "path": "./node_modules/cz-conventional-changelog"
        }
    }
}
```

in shell
```
git add -A
git-cz
```

## generate changlog

```
"genlog": "conventional-changelog -p angular -i .github/CHANGELOG.md -s"
```

And

```
yarn genlog
```