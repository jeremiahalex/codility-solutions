# [Brackets](https://codility.com/programmers/lessons/7-stacks_and_queues/)
Determine whether a given string of parentheses is properly nested.

### Solution (JavaScript)
To solve this we can push each open bracket we encounter on a stack and pop when we encounter a closing bracket. However, if the closing bracket doesn't match then it is not properly nested. Likewise if there are brackets left on the stack then it is also not properly nested.

__[Test Score: 100%](https://codility.com/demo/results/trainingA7SXHS-QH8/)__

```js
function solution(S) {
    let brackets = []
    for (let i = 0; i < S.length; ++i){
        if ( /[{[(]{1}/.test(S[i]) ) {
            brackets.push(S[i])   
        } else if ( /[})\]]{1}/.test(S[i]) ) {
            if ( S[i] === ")" && brackets[brackets.length-1] !== "(" ) return 0
            if ( S[i] === "}" && brackets[brackets.length-1] !== "{" ) return 0
            if ( S[i] === "]" && brackets[brackets.length-1] !== "[" ) return 0
            //else ok to remove bracket
            brackets.pop()
        }
    }
    
    return brackets.length === 0 ? 1 : 0
}
```
