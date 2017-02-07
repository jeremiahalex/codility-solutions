# [Triangle](https://codility.com/programmers/lessons/6-sorting/)
Determine whether a triangle can be built from a given set of edges.

### Solution (JavaScript)
The insight required here is that for a triange to occur, the numbers must be relatively close in value. If we sort the array, then we can get the numbers in sets of 3 with their closest neightbour, if any are a triangle then we have a solution.

__[Test Score: 100%](https://codility.com/demo/results/trainingDW5ZX4-6Y6/)__

```js
function solution(A) {
    A.sort((a,b) => a-b)
    
    for (let i = 2; i < A.length; ++i) {
        if (A[i] + A[i-1] <= A[i-2] ) continue
        if (A[i] + A[i-2] <= A[i-1] ) continue
        if (A[i-1] + A[i-2] <= A[i] ) continue
        return 1
    }
    
    return 0
}
```
