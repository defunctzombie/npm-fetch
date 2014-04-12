# npm-fetch

Fetch npm modules.

[![Build Status](https://travis-ci.org/ForbesLindesay/npm-fetch.png?branch=master)](https://travis-ci.org/ForbesLindesay/npm-fetch)
[![Dependency Status](https://gemnasium.com/ForbesLindesay/npm-fetch.png)](https://gemnasium.com/ForbesLindesay/npm-fetch)
[![NPM version](https://badge.fury.io/js/npm-fetch.png)](http://badge.fury.io/js/npm-fetch)

## Usage

Example fetching a tarball to a file.

```js
var fetch = require('npm-fetch');
var pkgStream = fetch('npm-fetch', '0.0.1');

pkg
.syphon(barrage(fs.createWriteStream('/path/to/pkg.tar.gz')))
.wait(function(err) {
 // called when done
});
```

## API

### fetch(name, spec, options)

Fetch the package as a tarball and return a [barrage](https://www.npmjs.org/package/barrage) stream for the tarball payload.

 - `name` the name of the package as a string
 - `spec` a string which can be:
   - a version, version range or tag if the module is in the npm repository
   - a url with `https` or `http` as the scheme, where the module is hosted somewhere as a tarball
   - a git url, where the module will be cloned as a git repository
   - a GitHub specifier of the form `username/reponame#tag-name` where `#tag-name` is optional and defaults to `#master`

The `name` is what you would find on the left side of a dependency in package.json and the `spec` is what would be on the right side.
