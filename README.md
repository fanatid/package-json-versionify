package-json-versionify
-------

Browserify transform to strip everything from `package.json` except for
the `"version"` field.


    npm install --save package-json-versionify


**Problem:** you want to ship a library, and do something like:

```js
MyLibrary.version = require('./package.json').version;
```

Unfortunately, if you do this, then your entire `package.json` will be included
in the output Browserify bundle, which will increase your bundle size.

This transform simply removes everything from `package.json` except for the
`"version"` field. So when you `require('./package.json')`, you get something
like:

```js
{
  "version": "1.0.0"
}
```