# [MaxDoubleSlice](https://codility.com/programmers/lessons/9-maximum_slice_problem/)
Find the maximal sum of any double slice.

### Solution (JavaScript) - Failing on Randomised Tests
The question is actually asking us to find the two biggest slices that have a single space between them (Y). We can loop through our array and create a list of the best slices on the left upto a particular pivot (y) and then the best slices on the right from that same pivot. Afterwards we then pick the pair that sums to the greatest total.

__[Test Score: 61%](https://codility.com/demo/results/trainingCQS3XV-ZUR/)__

```js
function solution(A) {
    let zMax = A.length - 2
    let leftSlices = new Array(zMax).fill(0)
    let rightSlices = new Array(zMax).fill(0)
    let leftSlice = 0
    let leftSliceBiggest = 0
    let leftSlicePreviousBiggest = 0
    let rightSlice = 0
    let rightSliceBiggest = 0
    let rightSlicePreviousBiggest = 0
    for ( let x = 1; x < zMax; ++x ) {
        // if the total drops below zero then we're are better off starting from scratch with a new slice
        // and if the slice total is larger than our largest slice, then store it and move the end point
        leftSlice = Math.max( 0, leftSlice + A[x] )
        leftSliceBiggest = Math.max( leftSliceBiggest, leftSlice )
        
        leftSlices[x] = Math.max( leftSlicePreviousBiggest, leftSliceBiggest )
        leftSlicePreviousBiggest = leftSlices[x]
        
        // more concise form of the same slice logic - but from the opposite side of the array
        let z = A.length - x
        rightSlice = Math.max( 0, rightSlice + A[z-1] )
        rightSliceBiggest = Math.max( rightSliceBiggest, rightSlice )
        
        let index = zMax - 1 - x
        rightSlices[index] = Math.max( rightSlicePreviousBiggest, rightSliceBiggest )
        rightSlicePreviousBiggest = rightSlices[index]
    }
    let total = 0
    for ( let i = 0; i < leftSlices.length; ++i ) {
        total = Math.max( leftSlices[i] + rightSlices[i], total )
    }
    
    return total
}

```
