<a href="http://promisesaplus.com/">
    <img src="http://promisesaplus.com/assets/logo-small.png" alt="Promises/A+ logo"
         title="Promises/A+ 1.1 compliant" align="right" />
</a>
[![Build Status](https://travis-ci.org/petkaantonov/bluebird.svg?branch=master)](https://travis-ci.org/petkaantonov/bluebird)
[![coverage-98%](http://img.shields.io/badge/coverage-98%-brightgreen.svg?style=flat)](http://petkaantonov.github.io/bluebird/coverage/debug/index.html)

**Got a question?** Join us on [stackoverflow](http://stackoverflow.com/questions/tagged/bluebird), the [mailing list](https://groups.google.com/forum/#!forum/bluebird-js) or chat on [IRC](https://webchat.freenode.net/?channels=#promises)

# Introduction

Bluebird is a fully featured promise library with focus on innovative features and performance

See the [**bluebird website**](http://bluebirdjs.com/docs/getting-started.html) for further documentation, references and instructions. See the [**API reference**](http://bluebirdjs.com/docs/api-reference.html) here.

For bluebird 2.x documentation and files, see the [2.x tree](https://github.com/petkaantonov/bluebird/tree/2.x).

# Questions and issues

The [github issue tracker](https://github.com/petkaantonov/bluebird/issues) is **_only_** for bug reports and feature requests. Anything else, such as questions for help in using the library, should be posted in [StackOverflow](http://stackoverflow.com/questions/tagged/bluebird) under tags `promise` and `bluebird`.



## Thanks

Thanks to BrowserStack for providing us with a free account which lets us support old browsers like IE8. 

# License

The MIT License (MIT)

Copyright (c) 2013-2016 Petka Antonov

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

Include Bluebird - it's a superset of ES6 promises and you can swap it right inside, it has a richer API, it's faster and it has amazing stack traces. It's built with debugging in mind and includes great error handling facilities.

Once you've included Bluebird, call:

Promise.longStackTraces();
Which will slow it down a bit (it'll still be very fast) and will give you amazing error messages. For example:

Promise.resolve().then(function outer() {
    return Promise.resolve().then(function inner() {
        return Promise.resolve().then(function evenMoreInner() {
            a.b.c.d()
        });
    });
});
In native promises - this will be a silent failure and will be very hard to debug - with Bluebird promises this will show a big red error in your console by default giving you:

ReferenceError: a is not defined
    at evenMoreInner (<anonymous>:6:13)
From previous event:
    at inner (<anonymous>:5:24)
From previous event:
    at outer (<anonymous>:4:20)
From previous event:
    at <anonymous>:3:9
    at Object.InjectedScript._evaluateOn (<anonymous>:581:39)
    at Object.InjectedScript._evaluateAndWrap (<anonymous>:540:52)
    at Object.InjectedScript.evaluate (<anonymous>:459:21)
Once you're done debugging - you can swap it out and go back to native promises. Personally I value knowing I have errors in production so I don't recommend it but it's certainly doable.
