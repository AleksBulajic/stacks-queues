![GA LOGO](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

## Stacks and Queues Challenge: Bracket Matching

### Setup

1. **Fork and Clone This Repository**

2. **Install Dependencies**

   Navigate into the project directory and install the necessary dependencies by running:

   ```bash
   npm install
   ```

3. **Complete the Exercises**

   - Complete your exercises in the `bracketMatcher()` function in `stacks-and-queues.js`. 

4. **Check Your Work**

   There are test files for each of these exercises with the same name. Use these test files to check if your sorting algorithms are implemented correctly.
   To verify your solutions, run the test files by executing:

   ```bash
   npm test
   ```

## Intro


Surely by now you've made an error in your code that seemed impossible to track down. But in the end, the root of all that trouble might have been something as simple as a missing (or extra) curly brace `}`. This example might be all too relatable (or painful)!

One really convenient application for LIFO (Last In First Out) structures is matching brackets. That's because every time you encounter a closing bracket, it needs to match the **most recently used** open bracket.

For example, this is valid: Nesting is OK!

```js
[]{}(({}))
```

But this one doesn't work:

```js
{(})
```

This is because the closing `}` you encounter doesn't close an opening `{` but instead is trying to close `(`, which doesn't match!

## Getting Started

Create a method in JavaScript called `bracketMatcher()` that takes a string as an input. The function should determine if all brackets are correctly matching and properly nested. The return value of the function is `true` if the bracket combination is valid and `false` if it is not. This is a tool that could be used to detect syntax errors in your code!

It should check for the following: `[ ]`, `{ }`, and `( )`. Anything else (numbers, letters, punctuation, whitespace, etc.) should be skipped/ignored. This is a valid bracket sequence:

```js
abc(123)!{def}456:D
```

Once you ignore or remove all of the other characters, it just becomes:

```js
(){}
```

<br>
<br>

## Hints : Caution Spoilers Below ⚠️

Need some help getting started? Here are some hints for inspiration.

**HINT 1**

To process each character in the input string one at a time, you can split the string into an array of characters using `split('')`. Then, loop through the array with a `for` loop. Here's how you can do it:

```javascript
let characters = input.split('');

for (let i = 0; i < characters.length; i++) {
  // YOUR CODE HERE
  // Inside this loop, characters[i] is the current character.
}
```

**HINT 2**

This problem involves matching brackets. Once we find a closing bracket that matches an opening bracket, we don't need to keep track of it anymore. Therefore, we only need to keep track of the opening brackets. We can ignore any non-bracket characters. Which data structure is best suited for holding opening brackets?

**HINT 3**

A stack is ideal for this problem because we always want to close the most recently opened bracket. For example, if we encounter `(`, `{`, `}`, and `)` in that order, it is valid. Here's the process in pseudocode:

1. See `(`. Push it onto the stack.
2. See `{`. Push it onto the stack.
3. See `}`. Pop from the stack and check for a match.
4. It matches! `{` is the opening bracket for `}`, so continue.
5. See `)`. Pop from the stack and check for a match.
6. It matches! `(` is the opening bracket for `)`, so continue.
7. No more items in the stack.
8. Return `true` (no errors found, so it's valid!).

If the brackets do not match, return `false`. For example, `{`, `(`, `}`, and `)` is not valid. Here's why:

1. See `{`. Push it onto the stack.
2. See `(`. Push it onto the stack.
3. See `}`. Pop from the stack and check for a match.
4. It doesn't match! Return `false`.

**HINT 4**

To determine if a character is an opening or closing bracket, you can use these helper functions:

```javascript
const isOpening = (character) => '{(['.indexOf(character) !== -1;
const isClosing = (character) => '})]'.indexOf(character) !== -1;
```

**HINT 5**

You might encounter a test case like `bracketMatcher('abc(123')` that should return `false` because an opening bracket with no closing bracket is invalid. Ensure the stack is empty at the end of the function to catch this case.

**HINT 6**

We need to ensure that each type of bracket ((), {}, []) is matched correctly. While you could use a series of `if/else` statements, a more readable approach is to use a JavaScript object to map opening brackets to their corresponding closing brackets.

One way is to use strings:

```javascript
let openings = '{([';
let closings = '})]';

let isMatch = (opening, closing) =>
  openings.indexOf(opening) === closings.indexOf(closing);
```

A more readable approach is to use an object:

```javascript
const brackets = {
  '{': '}',
  '(': ')',
  '[': ']',
};

if (brackets[characters[i]] !== stack.peek()) {
  // handle mismatch
}
```
