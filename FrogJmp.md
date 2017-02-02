# [FrogJmp](https://codility.com/programmers/lessons/3-time_complexity/)
Count minimal number of jumps from position X to Y.

### Solution (JavaScript)
A simple challenge that requires a basic calculation rather than any form of iteration.

__[Test Score: 100%](https://codility.com/demo/results/trainingMHVCPG-CKS/)__

```js
function solution(X, Y, D) {
    return Math.ceil((Y-X)/D)
}
```
