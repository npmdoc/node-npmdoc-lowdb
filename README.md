# npmdoc-lowdb

#### api documentation for  [lowdb (v0.16.2)](https://github.com/typicode/lowdb)  [![npm package](https://img.shields.io/npm/v/npmdoc-lowdb.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-lowdb) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-lowdb.svg)](https://travis-ci.org/npmdoc/node-npmdoc-lowdb)

#### JSON database for Node and the browser powered by lodash API

[![NPM](https://nodei.co/npm/lowdb.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/lowdb)

- [https://npmdoc.github.io/node-npmdoc-lowdb/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-lowdb/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-lowdb/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-lowdb/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-lowdb/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-lowdb/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Typicode"
    },
    "browser": {
        "./src/storages/file-sync.js": "./src/storages/browser.js",
        "./lib/storages/file-sync.js": "./lib/storages/browser.js"
    },
    "bugs": {
        "url": "https://github.com/typicode/lowdb/issues"
    },
    "dependencies": {
        "graceful-fs": "^4.1.3",
        "is-promise": "^2.1.0",
        "lodash": "4",
        "steno": "^0.4.1"
    },
    "description": "JSON database for Node and the browser powered by lodash API",
    "devDependencies": {
        "babel-cli": "^6.2.0",
        "babel-eslint": "^7.0.0",
        "babel-loader": "^6.2.2",
        "babel-polyfill": "^6.9.1",
        "babel-preset-es2015": "^6.1.18",
        "babel-preset-stage-3": "^6.3.13",
        "babel-register": "^6.9.0",
        "husky": "^0.13.0",
        "lodash-id": "^0.13.0",
        "pkg-ok": "^1.0.1",
        "ramda": "^0.23.0",
        "rimraf": "^2.5.4",
        "sinon": "^1.17.2",
        "standard": "^8.5.0",
        "tap-spec": "^4.1.1",
        "tape": "^4.2.2",
        "tempfile": "^1.1.1",
        "webpack": "^2.2.1"
    },
    "directories": {},
    "dist": {
        "shasum": "a2a976eb66ec57797291970f3c87cdb61126fa3a",
        "tarball": "https://registry.npmjs.org/lowdb/-/lowdb-0.16.2.tgz"
    },
    "engines": {
        "node": ">= 0.12"
    },
    "gitHead": "4a76af0f79d900043fd5ebf0ff4b378e8404bd89",
    "homepage": "https://github.com/typicode/lowdb",
    "keywords": [
        "flat",
        "file",
        "local",
        "database",
        "storage",
        "JSON",
        "lo-dash",
        "lodash",
        "underscore",
        "localStorage",
        "embed",
        "embeddable"
    ],
    "license": "MIT",
    "main": "./lib/main.js",
    "maintainers": [
        {
            "name": "typicode"
        }
    ],
    "name": "lowdb",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git://github.com/typicode/lowdb.git"
    },
    "scripts": {
        "build": "npm run build:lib && npm run build:dist",
        "build:dist": "rimraf dist && webpack && webpack -p",
        "build:lib": "rimraf lib && babel src --out-dir lib",
        "fix": "standard --fix",
        "precommit": "npm test",
        "prepublish": "npm run build && pkg-ok",
        "tape": "tape -r babel-register -r babel-polyfill test/*.js | tap-spec",
        "test": "npm run tape && standard"
    },
    "standard": {
        "parser": "babel-eslint"
    },
    "version": "0.16.2",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
