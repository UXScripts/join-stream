# join-stream

Intersperse stream chunks with separators.

# example

``` js
var joinStream = require('join-stream');
var split = require('es').split;

process.stdin
    .pipe(split())
    .pipe(joinStream(','))
    .pipe(process.stdout)
;
```

```
$ node example/comma.js
abc
def
hi
jkl
^D
abc,def,hi,jkl
```

# methods

``` js
var joinStream = require('join-stream')
```

## joinStream(sep, opts={})

Return a [through stream](https://github.com/substack/stream-handbook#through)
that inserts the string or buffer separator `sep` between `'data'` chunks.

If `opts.end` is truthy, insert the separators immediately after `'data'` events
are received and add a separator after the last element. Otherwise add the
separators only after the next element has been received and don't add a
separator after the last element.

# install

With [npm](https://npmjs.org) do:

```
npm install join-stream
```

# license

MIT