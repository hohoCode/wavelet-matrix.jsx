wavelet-matrix.jsx
===========================================

[![Build Status](https://travis-ci.org/shibukawa/wavelet-matrix.jsx.png)](https://travis-ci.org/shibukawa/wavelet-matrix.jsx)

Synopsis
---------------

WaveletMatrix implementation for JS/JSX/AMD/CommonJS

Motivation
---------------

This code is a part of [Oktavia](http://oktavia.info). This is a heart of FM-index search engine.
WaveletMatrix provides O(1) algorithm for the following operation:

* Rank: count the number of specified character in specified range.

Current implementation doesn't provide Select operation.

* http://www.dcc.uchile.cl/~gnavarro/ps/spire12.4.pdf

Code Example
---------------

### Use from JSX

```js
import "wavelet-matrix.jsx";

class _Main {
    static function main(argv : string[]) : void {
        var wm = new WaveletMatrix();
        wm.build("abracadabra mississippi");
        wm.rank(10, "a".charCodeAt(0));
    }
}
```

### Use from node.js

```js
var WaveletMatrix = require('wavelet-matrix.common.js').WaveletMatrix;
```

### Use from require.js

```js
// use wavelet-matrix.amd.js
define(['wavelet-matrix.js'], function (waveletmatrix) {

    var wm = new WaveletMatrix.WaveletMatrix();
});
```

### Use via standard JSX function

```html
<script src="wavelet-matrix.js" type="text/javascript"></script>
<script type="text/javascript">
window.onload = function () {
    var WaveletMatrix = JSX.require("lib/wavelet-matrix.jsx").WaveletMatrix;
});
</script>
```

### Use via global variables

```html
<script src="wavelet-matrix.global.js" type="text/javascript"></script>
<script type="text/javascript">
window.onload = function () {
    var wm = new WaveletMatrix();
});
</script>
```

Installation
---------------

```sh
$ npm install wavelet-matrix.jsx
```

If you want to use this library from other JSX project, install like the following:

```sh
$ npm install wavelet-matrix.jsx --save-dev
```

or add like these lines to your parent project's `package.json`:

```js
   devDependencies: {
       "wavelet-matrix.jsx": "~0.3.0"
   },
   peerDepenencies: {
       "wavelet-matirx.jsx": "~0.3.0"
   }
```

And add `node_modules/wavelet-matrix.jsx/src` as a search path. You should add `peerDepenencies` if your product is library.

API Reference
------------------

### class WaveletMatrix()

Constructor.

### function WaveletMatrix#bitsize() : int

Return current bit-size setting. Default value is 16.

### function WaveletMatrix#setMaxCharCode(code : int) : void

Set max character code stored in this matrix. Default value is 65535 (UCS2 character code limit).
If you use only latin-1, set `256` and save memory.

### function WaveletMatrix#maxCharCode() : int

Return max character code.

### function WaveletMatrix#clear() : void

Clear matrix.

### function WaveletMatrix#build(source : string) : void

Build wavelet matrix. You should call this before using `rank()` or `rankLessThan()`.

### function WaveletMatrix.size() : int

Return input string size.

### function WaveletMatrix#count(code : int) : int

Return the number of specified character in the source string.

### function WaveletMatrix#get(i : int) : int

Return the x-th character.

### function WaveletMatrix#rank(i : int, code : int) : int

Count the number of specified character before the specified position.

### function WaveletMatrix#rankLessThan(i : int, code : int) : int

Count the number of the character that is smaller than specified character before the specified position.

### function WaveletMatrix#dump(output : BinaryOutput) : void

Export WaveletMatrix.

### function WaveletMatrix#load(input : BinaryInput) : void

Import WaveletMatrix.

Development
-------------

## JSX

Don't be afraid [JSX](http://jsx.github.io)! If you have an experience of JavaScript, you can learn JSX
quickly.

* Static type system and unified class syntax.
* All variables and methods belong to class.
* JSX includes optimizer. You don't have to write tricky unreadalbe code for speed.
* You can use almost all JavaScript API as you know. Some functions become static class functions. See [reference](http://jsx.github.io/doc/stdlibref.html).

## Setup

To create development environment, call following command:

```sh
$ npm install
```

## Repository

* Repository: git://github.com/shibukawa/wavelet-matrix.jsx.git
* Issues: https://github.com/shibukawa/wavelet-matrix.jsx/issues

## Run Test

```sh
$ grunt test
```

## Build

```sh
$ grunt build
```

## Generate API reference

```sh
$ grunt doc
```

Author
---------

* shibukawa / yoshiki@shibu.jp

License
------------

MIT

Complete license is written in `LICENSE.md`.
