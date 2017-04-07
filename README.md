# api documentation for  [minify (v2.0.13)](http://coderaiser.github.io/minify)  [![npm package](https://img.shields.io/npm/v/npmdoc-minify.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-minify) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-minify.svg)](https://travis-ci.org/npmdoc/node-npmdoc-minify)
#### Minifier of js, css, html and img

[![NPM](https://nodei.co/npm/minify.png?downloads=true)](https://www.npmjs.com/package/minify)

[![apidoc](https://npmdoc.github.io/node-npmdoc-minify/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-minify_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-minify/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-minify/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-minify/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "coderaiser",
        "email": "mnemonic.enemy@gmail.com",
        "url": "https://github.com/coderaiser"
    },
    "bin": {
        "minify": "bin/minify.js"
    },
    "bugs": {
        "url": "https://github.com/coderaiser/minify/issues"
    },
    "dependencies": {
        "clean-css": "~3.4.1",
        "css-b64-images": "~0.2.5",
        "debug": "^2.3.0",
        "execon": "~1.2.0",
        "html-minifier": "^3.0.1",
        "rendy": "~1.1.0",
        "tomas": "~1.0.0",
        "try-catch": "~1.0.0",
        "uglify-js": "^2.7.0"
    },
    "description": "Minifier of js, css, html and img",
    "devDependencies": {
        "jscs": "^3.0.3",
        "jshint": "^2.8.0",
        "tape": "^4.2.2"
    },
    "directories": {},
    "dist": {
        "shasum": "e4f75cb34e919ef1ccc60bf4f2aec0b9b7863ab9",
        "tarball": "https://registry.npmjs.org/minify/-/minify-2.0.13.tgz"
    },
    "engines": {
        "node": ">= 0.8.0"
    },
    "gitHead": "eeaa345e390ff0029c8da18ba6aee404a9b498eb",
    "homepage": "http://coderaiser.github.io/minify",
    "keywords": [
        "minify",
        "minimize",
        "js",
        "css",
        "img",
        "html",
        "base64"
    ],
    "license": "MIT",
    "main": "lib/minify",
    "maintainers": [
        {
            "name": "coderaiser",
            "email": "mnemonic.enemy@gmail.com"
        }
    ],
    "name": "minify",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+ssh://git@github.com/coderaiser/minify.git"
    },
    "scripts": {
        "jscs": "jscs --esnext lib test",
        "jscs-fix": "jscs --fix lib test",
        "jshint": "jshint lib test",
        "lint": "npm run jshint && npm run jscs",
        "test": "tape test/minify.js"
    },
    "version": "2.0.13"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module minify](#apidoc.module.minify)
1.  [function <span class="apidocSignatureSpan">minify.</span>css (data, callback)](#apidoc.element.minify.css)
1.  [function <span class="apidocSignatureSpan">minify.</span>html (data, callback)](#apidoc.element.minify.html)
1.  [function <span class="apidocSignatureSpan">minify.</span>img (name, data, callback)](#apidoc.element.minify.img)
1.  [function <span class="apidocSignatureSpan">minify.</span>js (data, callback)](#apidoc.element.minify.js)



# <a name="apidoc.module.minify"></a>[module minify](#apidoc.module.minify)

#### <a name="apidoc.element.minify.css"></a>[function <span class="apidocSignatureSpan">minify.</span>css (data, callback)](#apidoc.element.minify.css)
- description and source-code
```javascript
css = function (data, callback) {
    var error, errorParse, dataOptimized;

    assert(data);
    assert(callback);

    if (!Clean)
        error   = ErrorMsg;
    else
        error   = tryCatch(function() {
            var min         = new Clean().minify(data);
            dataOptimized   = min.styles;
            errorParse      = min.errors[0];
        });

    callback(error || errorParse, dataOptimized);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.minify.html"></a>[function <span class="apidocSignatureSpan">minify.</span>html (data, callback)](#apidoc.element.minify.html)
- description and source-code
```javascript
html = function (data, callback) {
    var error;

    assert(data);
    assert(callback);

    if (!Minifier)
        error   = ErrorMsg;
    else
        error   = tryCatch(function() {
            data = Minifier.minify(data, Options);
        });

    callback(error, data);
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.minify.img"></a>[function <span class="apidocSignatureSpan">minify.</span>img (name, data, callback)](#apidoc.element.minify.img)
- description and source-code
```javascript
img = function (name, data, callback) {
    var dir         = path.dirname(name),
        dirRelative = dir + '/../';

    assert(name);
    assert(data);
    assert(callback);

    if (!B64img)
        callback(ErrorMsg);
    else
        B64img.fromString(data, dir, dirRelative, OPTIONS, function(error, css) {
            callback(null, css);
        });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.minify.js"></a>[function <span class="apidocSignatureSpan">minify.</span>js (data, callback)](#apidoc.element.minify.js)
- description and source-code
```javascript
js = function (data, callback) {
    var error, dataOptimized;

    assert(data);
    assert(callback);

    if (!uglify)
        error = ErrorMsg;
    else
        error = tryCatch(function() {
            dataOptimized = uglify.minify(data, {fromString: true}).code;
        });

    callback(error, dataOptimized);
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
