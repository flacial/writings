**Chapter 05: Coding by Composing**


**Function composition:** the formation of a new function by composing multiple ones

- Function composition follows the law of associativity. As a result, functions are extracted and bundled together.

Note: We should first partially apply built-in functions (map, filter, reduce...) that take more than one argument before composing them with other functions.

```js
const filter = curry((fn, arr) => arr.filter(fn));

const a = compose(b, c, d, filter(fn));
```


**Point-free:** the style of never mentioning what data a function works on.

- It helps to reduce the clutter by omitting the arguments in a function definition.

```js
const a = ['a', 'b', 'c', 'd', 'e', 'f']
const whatElement = i => console.log(i);

// not pointfree!
a.forEach(e => whatElement(e));

// pointfree
a.forEach(whatElement);


// not pointfree!
const aIsCrazy = (a) => a.join(' ').toLowerCase().replaceAll('a', '*!$%!')

// pointfree
const replaceAll = curry((t, r, str) => str.replaceAll(t, r))
const toLowerCase = s => s.toLowerCase()
const join = curry((s, str) => str.join(s))

const aIsCrazy = compose(replaceAll('a', '*!$%!'), toLowerCase, join(' '))

aIsCrazy(['amazon', 'potato']) // '*!$%!m*!$%!zon pot*!$%!to'
```


**unary:** a function that takes only one argument.

Example: `const multiplyBy2 = x => x * 2`