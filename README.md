# smart-eql [![Build Status](https://travis-ci.org/chaijs/deep-eql.png?branch=master)](https://travis-ci.org/chaijs/deep-eql) [![Coverage Status](https://coveralls.io/repos/chaijs/deep-eql/badge.png?branch=master)](https://coveralls.io/r/chaijs/deep-eql?branch=master)

Smart deep equality testing for Node.js.  This was forked from [deep-eql](https://github.com/chaijs/deep-eql), with the
addition of regex and function testing.

## Installation

`smart-eql` is available on [npm](http://npmjs.org).

    $ npm install --save smart-eql

## Usage

### Rules

- Strict equality for non-traversable nodes according to [egal](http://wiki.ecmascript.org/doku.php?id=harmony:egal).
  - `eql(NaN, NaN).should.be.true;`
  - `eql(-0, +0).should.be.false;`
- Arguments are not Arrays:
  - `eql([], arguments).should.be.false;`
  - `eql([], Array.prototype.slice.call(arguments)).should.be.true;`
- Use regex to test values:
  - `eql({a: /he.+world/}, {a: 'hello world'}).should.be.true;`
  - `eql('hxllo world', /he.+world/).should.be.false;`
