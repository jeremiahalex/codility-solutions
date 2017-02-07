# [CountDiv](https://codility.com/programmers/lessons/5-prefix_sums/)
Compute number of integers divisible by k in range [a..b].

### Solution (JavaScript)
If we calculate the floor of B/k and the ceiling on A/K, then the difference between those two values (+ 1) is the number of steps of K possible.

__[Test Score: 100%](https://codility.com/demo/results/trainingJ923KU-9FW/)__

```js
function solution(A, B, K) {
    let max = Math.floor(B/K)
    let min = Math.ceil(A/K)
    
    return max - min + 1
}
```
