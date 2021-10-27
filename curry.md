**Currying:** the process of breaking a function that takes multiple arguments, into a function that takes them one by one / The delay of arguments.


**How curry function work:**

```js
const curry = (baseFunction) => {
    // It's usually called arity.
    const baseFunctionArgsCount = baseFunction.length;

    return function $curry(...args) {
        const givenArgsCount = args.length;

/*
If the givenArgsCount is less than baseFunctionArgsCount, it means it must return another function to get the rest of the arguments and pass it all the previous arguments (...args).
*/
        if (givenArgsCount < baseFunctionArgsCount) {
/*
bind: return a copy of the given function (in our case, $curry) with a specified "this" value and arguments.
First argument (null): the value "this" will refer to. By passing "null" it'll refer to the $curry copy.
Second argument (...args): all the previous arguments will be passed as the $curry copy arguments.
*/
            return $curry.bind(null, ...args)
        }

/*
When the given arguments count is equal to the base fucnction arguments count, It'll call it with all the given arguments and return it.
*/

        return baseFunction.call(null, ...args)
    }
}

// baseFunctionArgsCount = 3
const add3Nums = (num1, num2, num3) => num1 + num2 + num3

const add3NumsC = curry(add3Nums)

// givenArgsCount = 1. It's less than baseFunctionArgsCount, so it'll return a function to get the rest of the arguments.
const addFirstNumToFn = add3NumsC(1) 

// givenArgsCount = 2. It'll return a function again.
const addSecondNumToFn = addFirstNumToFn(2)

// givenArgsCount = 3. It's equal to baseFunctionArgsCount, so it'll call add3Nums with all the arguments (1, 2, 3) and return its returned value.
const addThirdNumToFn = addSecondNumToFn(3)

console.log(addThirdNumToFn) // 6
```