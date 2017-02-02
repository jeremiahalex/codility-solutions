# [TapeEquilibrium](https://codility.com/programmers/lessons/3-time_complexity/)
Minimize the value |(A[0] + ... + A[P-1]) - (A[P] + ... + A[N-1])|.

### Solution (JavaScript)
We can do this in two loops - first we sum the array then we loop through each value of p, using the total and the sum of the left to calculate the value of the right hand side.

__[Test Score: 100%](https://codility.com/demo/results/trainingW2GYWF-TB2/)__

```js
function solution(A) {
    var total = A.reduce(( acc, cur ) => acc + cur)
    
    var leftSum = A[0]
    var smallestDiff = Number.MAX_SAFE_INTEGER 
    for (let p = 1; p < A.length; ++p){
       let rightSum = total - leftSum  
       let diff = Math.abs(leftSum - rightSum)
       if (diff < smallestDiff) {
           smallestDiff = diff
       }
       leftSum += A[p]
    }
    
    return smallestDiff
}
```
