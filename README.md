# HW2 JavaScript

## Why are closures useful in JavaScript? Give an example use case.

Closures are useful in JavaScript because they allow variables in parent functions to be accessed even after the parent function has executed.
An example use case would be a count variable in the parent function that needs to be accessed to determine the functionality of another function.

## When should you choose to use “let” or “const”

You should choose to use “let” when you want to reassign the variable later, and you should choose to use “const” when you want to do not want to reassign the variable later.

## Give an example of a common mistake related to hoisting and explain how to fix it.

A common mistake related to hoisting is when declaring a function using a function expression. The delcaration of the function is hoisted but not the initialization. This would result in an error if the function is executed, there would be a TypeError since the function would be undefined. This can be fixed by using function declarations which would hoist the declaration and the initialization of the function.

## What will the outcome of each console.log() be after the function calls? Why?

```js
const arr = [1, 2];
function foo1(arg) {
  arg.push(3);
}
foo1(arr);
console.log(arr);

function foo2(arg) {
  arg = [1, 2, 3, 4];
}
foo2(arr);
console.log(arr);

function foo3(arg) {
  let b = arg;
  b.push(3);
}
foo3(arr);
console.log(arr);

function foo4(arg) {
  let b = arg;
  b = [1, 2, 3, 4];
}
foo4(arr);
console.log(arr);
```

### Output

```console
[1, 2, 3]
[1, 2, 3]
[1, 2, 3, 3]
[1, 2, 3, 3]
```

`arg` in `foo1(arg)` holds a reference to the same array as arr, so when `arg.push(3)` is executed, so when `arg.push(3);` is executed 3 is pushed to the `[1, 2]`array which is referenced by both arg and arr, and now becomes `[1, 2, 3]`.

In `foo2(arg)`, when `arg` is assigned to `[1, 2, 3, 4]`, it now references the `[1, 2, 3, 4]` array instead of array `arr`. `arr` is not changed so the output remains the same.

`arg` in `foo3(arg)` holds a reference to the same array as arr, so when `let b = arg;` is executed, `b` now also references the same array as `arr` and `arg`. So when `b.push(3);` is executed, 3 is pushed onto the `[1, 2, 3]` array which is referenced by `arg`, `arr`, and `b`, and now becomes `[1, 2, 3, 3]`.

In `foo4(arg)`, when `b = [1, 2, 3, 4]` is executed, b now references this new array. Therefore when `console.log(arr)` is run, the output remains the same as `arr` has not been changed.
