# [FrogRiverOne](https://codility.com/programmers/lessons/4-counting_elements/)
Find the earliest time when a frog can jump to the other side of a river.

### Solution (JavaScript)
Similar to the previous problem, our approach is to loop through A and everytime we encounter a position store it in a second array along with the time, effectively reversing the array. We can then loop through the second array and find the maximum time value before we get to X
    
__[Test Score: 100%](https://codility.com/demo/results/training3D3DBZ-46Q/)__

```js
function solution(X, A) {
    let B = []
    
    for (let i = 0; i < A.length; ++i) {
        if ( !B[A[i]] ) B[A[i]] = i
    }
    
    let max_time = -1
    for (let i = 1; i <= X; ++i) {
        if ( typeof B[i] === "undefined" ) return -1
        if ( B[i] > max_time ) max_time = B[i] 
    }
    
    return max_time
}
```
