# [PermMissingElem](https://codility.com/programmers/lessons/3-time_complexity/)
Find the missing element in a given permutation.

### Solution (JavaScript)
A simple solution is to have a second array that stores the found values. We then check that array for the first value not found.

__[Test Score: 100%](https://codility.com/demo/results/trainingPCKE36-F63/)__

```js
function solution(A) {
    let B = Array(A.length+2).fill(false)

    // loop through A and set the indices true in B
    for (let i = 0; i < A.length; ++i){
        val = A[i]
        B[val] = true  
    }
    
    // next we find the first false value in B and return it
    for (let i = 1; i < B.length; ++i){
        if (B[i] === false) return i  
    }
    
    return 0
}
```

### Alternative Solution (JavaScript)
A more elegant solution is to work out the expected total of the array and the actual total of the values in it. The differenece is the missing number.

__[Test Score: 100%](https://codility.com/demo/results/trainingNUJKUF-8PG/)__

```js
function solution(A) {
    var expectedTotal = 0
    var actualTotal = 0
    
    for (var i = 0; i < A.length; ++i){
        actualTotal += A[i]
        expectedTotal += i + 1
    }
    expectedTotal += A.length + 1
    return expectedTotal - actualTotal
}
```
