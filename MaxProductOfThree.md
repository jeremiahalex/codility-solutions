# [MaxProductOfThree](https://codility.com/programmers/lessons/6-sorting/)
Maximize A[P] * A[Q] * A[R] for any triplet (P, Q, R).

### Solution (JavaScript)
 We can again start this solution by sorting, and taking the three largest numbers to multiply. There is an edge case however that we need to accomodate for. Two negatives make a positive, so the two lowest numbers (if negative) multiplied by the largest number could also be the biggest.

__[Test Score: 100%](https://codility.com/demo/results/trainingECATBF-VJK/)__

```js
function solution(A) {
    A.sort((a,b) => a-b)
    
    let last = A.length - 1
    return Math.max(A[0]*A[1]*A[last], A[last]*A[last-1]*A[last-2])
}
```
