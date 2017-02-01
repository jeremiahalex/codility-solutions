# [OddOccurrencesInArray](https://codility.com/programmers/lessons/2-arrays/)
Find value that occurs in odd number of elements.

__[Test Score: 100%](https://codility.com/demo/results/trainingWEAFQ4-KP5/)__

### Solution (JavaScript)
```js
function solution(A) {
    // one option is to sort the array and then find the first odd sequence
    var sorted = A.sort((a,b) => {
      return a - b  
    })
    
    var lastNumber = sorted[0]
    var count = 1
    for (var i = 1; i < sorted.length; ++i){
        if (sorted[i] == lastNumber) ++count
        else {
            if (count % 2 !== 0) return lastNumber
            else {
                lastNumber = sorted[i]
                count = 1
            }
        }
    }
    
    // to get here we must have had only 1 number in the array, so just return that
    return lastNumber
}
```
