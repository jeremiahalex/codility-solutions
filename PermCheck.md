# [PermCheck](https://codility.com/programmers/lessons/4-counting_elements/)
Check whether array A is a permutation.

### Solution (JavaScript)
This problem can easily be solved using a second array to track the found numbers and their occurance. We can then loop through and exit if a number is missing or occurs more than once.
        
__[Test Score: 100%](https://codility.com/demo/results/trainingE86CTY-UY8/)__

```js
function solution(A) {
    let B = []
    for (let i = 0; i < A.length; ++i) {
        B[A[i]] = ( B[A[i]] || 0 ) + 1    
    }
    
    for (let i = 1; i <= A.length; ++i) {
        if ( B[i] !== 1 ) return 0
    }
    
    return 1
}
```
