# [MaxProfit](https://codility.com/programmers/lessons/9-maximum_slice_problem/)
Given a log of stock prices compute the maximum possible earning.

### Solution (JavaScript)
Similar to other problems in this section we are still trying to find a maximal slice. The difference is that rather than taking the number itself we want to track the profit created by comparing that number against the bought price.
__[Test Score: 100%](https://codility.com/demo/results/training7EH768-5EZ/)__

```js
function solution(A) {
    let boughtPrice = A[0]
    let sliceProfit = 0
    let maxProfit = 0
    for (let i = 0; i < A.length; ++i) {
        let profit = A[i] - boughtPrice
        // if the profit is below zero then we reset our slice as it will no longer yield the best return.
        if ( profit < 0 ) {
            boughtPrice = A[i]
            sliceProfit = 0
        } else {
            sliceProfit = Math.max(sliceProfit, profit)
        }
    
        maxProfit = Math.max(maxProfit, sliceProfit)
    }
    
    return maxProfit
}
```
