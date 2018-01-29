# yarn-is-weird

## Environment

This was tested using macOS 10.13.2. 

```bash=
$ yarn --version 
1.3.2
```

## 1. Install NPM dependencies

```bash=
$ yarn install
```

Note how `./node_modules` contains `leftpad`. 

## 2. Test `./src/index.js`

```bash=
$ node ./src/index.js 
0001
```

## 3. Create a build, e.g. for AWS

```bash=
$ yarn build 
yarn run v1.3.2
$ rm -rf ./out && mkdir -p ./out && yarn install --production --pure-lockfile --modules-folder ./out/node_modules 
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
[4/4] 📃  Building fresh packages...
✨  Done in 0.83s.
```

## 4. Test `./src/index.js` again

```bash=
$ node ./src/index.js 
module.js:557
    throw err;
    ^

Error: Cannot find module 'leftpad'
```

Note that `./node_modules` is now empty!

```bash=
$ ls ./node_modules/
```

# Question

Why does `yarn install` on another target folder clear the default `node_modules`?
