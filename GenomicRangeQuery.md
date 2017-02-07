# [GenomicRangeQuery](https://codility.com/programmers/lessons/5-prefix_sums/)
Find the minimal nucleotide from a range of sequence DNA.

### Solution (JavaScript)
Our approach here is to keep track of the the total amount of each impact founter incounted in a string up to a certain point. Subtracting the values for each impact factor between two points we can know how many occur in a given slice and find the lowest non zero.

__[Test Score: 100%](https://codility.com/demo/results/trainingN34VW5-3NE/)__

```js
function solution(S, P, Q) {
    let newString = S.replace(/A/g,'1').replace(/C/g,'2').replace(/G/g,'3').replace(/T/g,'4')
    
    let sums = []
    for (let i = 0; i < newString.length; ++i) {
        let impact = Number.parseInt(newString[i])
        if ( sums[i-1] ) sums[i] = sums[i-1].slice() 
        else sums[i] = [0,0,0,0,0]
        sums[i][impact]++
    }
    
    let results = []
    for (let i = 0; i < P.length; ++i) {
        // to get the range we want to subtract from Q, everything that came before P. If the start then just subtract 0s
        let right = sums[Q[i]]
        let left = sums[P[i]-1]
        if ( typeof left === 'undefined' )  left = [0,0,0,0,0]
        
        let min = 5
        for (let j = 1; j < 5; ++j){
            let diff = right[j] - left[j]
            if ( diff > 0 && j < min ) min = j
        }
        results.push(min)
    }
    
    return results
}
```
