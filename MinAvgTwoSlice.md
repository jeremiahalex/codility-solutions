# [MinAvgTwoSlice](https://codility.com/programmers/lessons/5-prefix_sums/)
Find the minimal average of any slice containing at least two elements.

### Solution (JavaScript)
With the insight that the slice will have a maximum length of 3, this problem is easy to solve in O(N). This logic behind this is that anything above 3 is actually a combination of smaller slices of 2 or 3, and one of those will be smaller. Using this insight the problem is solved by stepping through the array in slices of 2-3.

__[Test Score: 100%](https://codility.com/demo/results/trainingNRK6NX-GW2/)__

```js
function solution(A) {
    var lowestAverage = null
    var lowestIndex = 0
    for (let i = 0; i < A.length-1; ++i) {
        var min = (A[i] + A[i+1]) / 2
        if ( i < A.length-2 ) {
            min = Math.min(min,(A[i] + A[i+1] + A[i+2]) / 3)
        }
        if ( lowestAverage === null || min < lowestAverage ) {
            lowestAverage = min
            lowestIndex = i
        }
    }
    
    return lowestIndex
}
```
