<!--

@license Apache-2.0

Copyright (c) 2022 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# setter

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Return an accessor function for setting an element in an indexed array-like object.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/array-base-setter
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var setter = require( '@stdlib/array-base-setter' );
```

#### setter( dtype )

Returns an accessor function for setting an element in an indexed array-like object.

```javascript
var arr = [ 1, 2, 3, 4 ];

var set = setter( 'generic' );
set( arr, 2, 10 );

var v = arr[ 2 ];
// returns 10
```

The returned accessor function accepts the following arguments:

-   **arr**: input array.
-   **idx**: element index.
-   **value**: value to set.

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   If provided an unsupported [`dtype`][@stdlib/array/dtypes], the function returns a default accessor function for accessing elements in any indexed array-like object; otherwise, the function returns an accessor function which should **only** be provided an array instance corresponding to `dtype` (e.g., if `dtype` is `'float64'`, the returned accessor function should only be provided instances of `Float64Array`).
-   Accessor functions do **not** verify that provided input arrays are array instances corresponding to `dtype`, as doing so would introduce performance overhead. If array instances corresponding to other data types are provided to an accessor function, JavaScript runtimes will consider the function polymorphic, potentially triggering de-optimization. In order to ensure maximum performance, **always** ensure that an accessor function is monomorphic.
-   Accessor functions do **not** perform bounds checking.
-   Accessor functions do **not** validate input values.
-   An _indexed_ array-like object is a data structure in which one accesses elements via integer indices using bracket `[]` notation (e.g., `Float64Array`, `Int32Array`, `Array`, etc). This is in contrast to an _accessor_ array-like object in which one accesses elements using `get` and `set` methods (e.g., `Complex64Array` and `Complex128Array`).

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var filled = require( '@stdlib/array-filled' );
var dtype = require( '@stdlib/array-dtype' );
var setter = require( '@stdlib/array-base-setter' );

var arr = filled( 1.0, 10, 'float64' );
setter( dtype( arr ) )( arr, 2, 100.0 );
console.log( arr );

arr = filled( 2.0, 10, 'float32' );
setter( dtype( arr ) )( arr, 2, 100.0 );
console.log( arr );

arr = filled( 3, 10, 'int32' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );

arr = filled( 4, 10, 'int16' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );

arr = filled( 5, 10, 'int8' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );

arr = filled( 6, 10, 'uint32' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );

arr = filled( 7, 10, 'uint16' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );

arr = filled( 8, 10, 'uint8' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );

arr = filled( 9, 10, 'uint8c' );
setter( dtype( arr ) )( arr, 2, 100 );
console.log( arr );
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/array-base-setter.svg
[npm-url]: https://npmjs.org/package/@stdlib/array-base-setter

[test-image]: https://github.com/stdlib-js/array-base-setter/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/array-base-setter/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/array-base-setter/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/array-base-setter?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/array-base-setter.svg
[dependencies-url]: https://david-dm.org/stdlib-js/array-base-setter/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/array-base-setter/tree/deno
[deno-readme]: https://github.com/stdlib-js/array-base-setter/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/array-base-setter/tree/umd
[umd-readme]: https://github.com/stdlib-js/array-base-setter/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/array-base-setter/tree/esm
[esm-readme]: https://github.com/stdlib-js/array-base-setter/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/array-base-setter/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/array-base-setter/main/LICENSE

[@stdlib/array/dtypes]: https://github.com/stdlib-js/array-dtypes

</section>

<!-- /.links -->
