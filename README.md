# commitporto

> commit porto oficial website

## Build Setup

``` bash
# install dependencies
yarn install

# serve with hot reload at localhost:8080
yarn start

# build for production with minification (deploys to gh-pages)
yarn deploy

```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## Archive previous edition

Older editions are archived in [alumniei/commitporto-previous](https://github.com/alumniei/commitporto-previous/). 

Each edition is under the path `/<YEAR>` (ex: 2019 edition is at https://previous.commitporto.com/2019)

To build a static version of the previous edition:
1. Change the favicon's `href` in the file `index.html` from `/static/favicon.ico` to `/<YEAR>/static/favicon.ico`
1. In the file `config/index.js` change the variable `build.assetsPublicPath` from `/` to `/<YEAR>/`
1. Change the path to the `Homepage`. In the file `src/router/index.js` change the `path` of the `Homepage` route from `/` to `/<YEAR>`
1. Build a static version with `$ yarn run build`
1. Copy the ALL generated content from the `dist` folder to the matching folder in the commitporto-previous repository `~/git/commitporto-previous/<YEAR>`
1. Commit & push. Github pages should deploy it automatically :)
