# api documentation for  [lowdb (v0.16.0)](https://github.com/typicode/lowdb)  [![npm package](https://img.shields.io/npm/v/npmdoc-lowdb.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-lowdb) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-lowdb.svg)](https://travis-ci.org/npmdoc/node-npmdoc-lowdb)
#### JSON database for Node and the browser powered by lodash API

[![NPM](https://nodei.co/npm/lowdb.png?downloads=true)](https://www.npmjs.com/package/lowdb)

[![apidoc](https://npmdoc.github.io/node-npmdoc-lowdb/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-lowdb_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-lowdb/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-lowdb/build/screen-capture.npmPackageListing.svg)



# package.json

```json

{
    "author": {
        "name": "Typicode",
        "email": "typicode@gmail.com"
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
        "json-parse-helpfulerror": "^1.0.3",
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
        "shasum": "0e3fb37332fa6189eca2d864e7ad9dc989359866",
        "tarball": "https://registry.npmjs.org/lowdb/-/lowdb-0.16.0.tgz"
    },
    "engines": {
        "node": ">= 0.12"
    },
    "gitHead": "e72e967f463a393d63599568593d87cd0d84810e",
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
            "name": "typicode",
            "email": "typicode@gmail.com"
        }
    ],
    "name": "lowdb",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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
    "version": "0.16.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module lowdb](#apidoc.module.lowdb)
1.  object <span class="apidocSignatureSpan">lowdb.</span>common

#### [module lowdb.common](#apidoc.module.lowdb.common)
1.  [function <span class="apidocSignatureSpan">lowdb.common.</span>init (db, key, source)](#apidoc.element.lowdb.common.init)



# <a name="apidoc.module.lowdb"></a>[module lowdb](#apidoc.module.lowdb)



# <a name="apidoc.module.lowdb.common"></a>[module lowdb.common](#apidoc.module.lowdb.common)

#### <a name="apidoc.element.lowdb.common.init"></a>[function <span class="apidocSignatureSpan">lowdb.common.</span>init (db, key, source)](#apidoc.element.lowdb.common.init)
- description and source-code
```javascript
function init(db, key, source) {
  var _ref = arguments.length > 3 && arguments[3] !== undefined ? arguments[3] : {},
      _ref$storage = _ref.storage,
      storage = _ref$storage === undefined ? defaultStorage : _ref$storage,
      _ref$format = _ref.format,
      format = _ref$format === undefined ? {} : _ref$format;

  db.source = source;

  // Set storage
  // In-memory only if no source is provided
  db.storage = _extends({}, memory, db.source && storage);

  db.read = function () {
    var s = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : source;

    var r = db.storage.read(s, format.deserialize);

    return isPromise(r) ? r.then(db.plant) : db.plant(r);
  };

  db.write = function () {
    var dest = arguments.length > 0 && arguments[0] !== undefined ? arguments[0] : source;

    var value = (arguments.length <= 1 ? 0 : arguments.length - 1) ? arguments.length <= 1 ? undefined : arguments[1] : db.getState
();

    var w = db.storage.write(dest, db.getState(), format.serialize);
    return isPromise(w) ? w.then(function () {
      return value;
    }) : value;
  };

  db.plant = function (state) {
    db[key] = state;
    return db;
  };

  db.getState = function () {
    return db[key];
  };

  db.setState = function (state) {
    db.plant(state);
    return db.write();
  };

  return db.read();
}
```
- example usage
```shell
...
      set(db.getState(), path, result);
      return db.write(source, result);
    };

    return getValue;
  }

  return common.init(db, '__state__', source, opts);
};
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
