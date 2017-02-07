# [Distinct](https://codility.com/programmers/lessons/6-sorting/)
Compute number of distinct values in an array.

### Solution (JavaScript)
If we sort the array then we are simply able to step through it and keep a counter of every time a new number is encountered.

__[Test Score: 100%](https://codility.com/demo/results/trainingECATBF-VJK/)__

```js
function solution(A) {
    A.sort((a,b) => a-b)
    let count = 0
    let previous = null
    A.forEach((e)=> {
        if (previous !== e) {
            count++
            previous = e
        }
    })
    
    return count
}
```
