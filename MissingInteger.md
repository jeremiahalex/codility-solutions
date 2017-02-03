# [MissingInteger](https://codility.com/programmers/lessons/4-counting_elements/)
Find the minimal positive integer not occurring in a given sequence.

### Solution (JavaScript)
Our solution here is to loop through the array and store a boolean value in a second array for each index that we find. We can then loop through and find the first index that is false. 
    
__[Test Score: 100%](https://codility.com/demo/results/trainingGK633G-7N4/)__

```js
function solution(A) {
    let B = []
    
    for (let i = 0; i < A.length; ++i) {
        if ( A[i] > 0 ) B[A[i]] = true
    }
    for (let i = 1; i < B.length; ++i) {
        if ( B[i] != true ) return i;
    }
    
    return B.length || 1 
}
```
