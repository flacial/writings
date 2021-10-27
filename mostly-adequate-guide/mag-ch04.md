**Chapter 04: Currying**


**Curry function:** A function that's called with fewer arguments that it expects, and returns a function that takes the rest of the arguments.
||Alt: the process of converting a function that takes multiple arguments into a function that takes them one by one.||


**Currying benefits**:

It makes it easy to call a function without passing all the arguments at once.
||> Calling it with both arguments all at once is a bit of a pain, however, so we can use a special helper function called `curry` to make defining and calling functions like this easier.||

It has the ability to transform any function that works on a single element into a function that works on multiple (e.g, objects).
||> We also have the ability to transform any function that works on single elements into a function that works on arrays.||


**Partial application:** a function that's given less arguments that it expects.
||> Giving a function fewer arguments than it expects is typically called partial application.||

**Partial application vs Currying:**
```js
const add = (a, b) => a + b;

// Partial application
const partialAdd = partial(add, 2);
partialAdd(2); // 4

// Currying
const curryAdd = curry(add);
const addOne = curryAdd(2);
const addTwo = addOne(2);
addTwo // 4
```

One of the partial application benefits is to remove a lot of boiler plate code.
||> Partially applying a function can remove a lot of boiler plate code.||


Currying is pure because each single argument returns a new function expecting the remaining arguments. Takes 1 input to 1 output.
||When we spoke about pure functions, we said they take 1 input to 1 output. Currying does exactly this: each single argument returns a new function expecting the remaining arguments. That, old sport, is 1 input to 1 output.||

Currying makes functional programming less verbose and tiresome.
||> It is a tool for the belt that makes functional programming less verbose and tedious.||