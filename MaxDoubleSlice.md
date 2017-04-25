# [MaxDoubleSlice](https://codility.com/programmers/lessons/9-maximum_slice_problem/)
Find the maximal sum of any double slice.

### Solution (JavaScript)
The question is actually asking us to find the two biggest slices that have a single space between them (Y). We can loop through our array and create a list of the best slices on the left upto a particular pivot (y) and then the best slices on the right from that same pivot. Afterwards we then pick the pair that sums to the greatest total.

The left side always ends at the pivot, so we need to decided where to start. We do this by checking if the total of a slice drops below zero in which case we reset it to zero (effectively repositioning x). The right side always starts from the pivot, so we decide where to end. Just like the left side, we do this by checking if the value drops below zero and resetting it (effectively repositioning z)

__[Test Score: 100%](https://codility.com/demo/results/trainingRGV6YK-SG4/)__

```js
function solution(A) {
    let max = A.length - 2
    let leftSlices = new Array(max).fill(0)
    let rightSlices = new Array(max).fill(0)
    let leftSlice = 0
    let rightSlice = 0
    for ( let y = 1; y < max; ++y ) {
        if ( leftSlice < 0 ) leftSlice = 0
        leftSlice += A[y]
        leftSlices[y] = Math.max( 0, leftSlice )
        
        // so we can use the same for loop, we do the right side in reverse
        let z = A.length - y
        if ( rightSlice < 0 ) rightSlice = 0
        rightSlice += A[z-1]
        let index = z-3
        rightSlices[index] = Math.max( 0, rightSlice )
    }
    let total = 0
    for ( let i = 0; i < leftSlices.length; ++i ) {
        total = Math.max( leftSlices[i] + rightSlices[i], total )
    }
    
    return total
}

```
