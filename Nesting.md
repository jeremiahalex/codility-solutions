# [Nesting](https://codility.com/programmers/lessons/7-stacks_and_queues/)
Determine whether given string of parentheses is properly nested.

### Solution (JavaScript)
This challenge is easily solved with a counter that behaves like a stack. Looping through the array, we increment with each opening brakcet, and decrement with each closing bracket. If it ever goes below zero or the final value isn't 0 then it is not properly nested

__[Test Score: 100%](https://codility.com/demo/results/trainingHTWQRH-YP8/)__

```js
function solution(S) {
    let brackets = 0
    for (let i = 0; i < S.length; i++) {
        if (S[i] === '(') brackets++
        else if (S[i] === ')') {
            brackets--
            if (brackets < 0) return 0
        }
    }
    
    return (brackets === 0) ? 1 : 0
}
```
