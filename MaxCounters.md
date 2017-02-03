# [MaxCounters](https://codility.com/programmers/lessons/4-counting_elements/)
Calculate the values of counters after applying all alternating operations: increase counter by 1; set value of all counters to current maximum.

### Solution (JavaScript)
To solve this, we know that we need to loop through all of A, in order to find each operation we must apply. We can keep track of the new minimum and only add it to an element when we go to change it. Adding a final loop at the end to ensure everything is greater or equal to the minimum.
           
__[Test Score: 100%](https://codility.com/demo/results/trainingNN3Z7Q-9DN/)__

```js
function solution(N, A) {
    let B = new Array(N).fill(0)
    
    let minValue = 0
    let maxValue = 0
    for (let i = 0; i < A.length; ++i){
        if ( A[i] > N ) {
            //then new base line is needed 
            minValue = maxValue
        } else {
            // check if less than the min
            let j = A[i] -1
            if ( B[j] < minValue ) B[j] = minValue
            // increase by one and check if we have a new max
            B[j]++
            if ( B[j] > maxValue ) maxValue = B[j]
        }
    }
    // one final loop through B to check nothing is less than the min
    for (let i = 0; i < B.length; ++i){
        if ( B[i] < minValue ) B[i] = minValue
    }
    
    return B
}
```
