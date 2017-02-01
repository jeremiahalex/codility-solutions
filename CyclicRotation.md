# [CyclicRotation](https://codility.com/programmers/lessons/1-iterations/)
Rotate an array to the right by a given number of steps.

### Solution (JavaScript)
Performance is not a concern so the simplest solution is probably the best. Just repeat the rotation process K times.

__[Test Score: 100%](https://codility.com/demo/results/trainingVRBP48-MUD/)__
```js
function solution(A, K) {
    // just repeat the rotation process k times
    for (let i = 0; i < K; ++i){
        // loop through the array and assign the previous value to the current position and store the current value as the next previous. previous starts as the last value as it loops round
        let previous = A[A.length -1] 
        for (let j = 0; j < A.length; ++j){
            let temp = A[j]
            A[j] = previous
            previous = temp
        }
    }    
    
    return A
}
```
### Alternative Solution (JavaScript)
An alternative solution is to construct an auxilary array, which then requires us to have only 1 loop.

__[Test Score: 100%](https://codility.com/demo/results/trainingR788SU-RME/)__
```js
function solution(A, K) {
    // An alternative solution is to construct an auxilary array, which then requires us to have only 1 loop
    let rotated = []
    for (let i = 0; i < A.length; ++i) {   
        let j = i + K
        if (j >= A.length) j = j % A.length 
        
        rotated[j] = A[i]
    }
    
    return rotated
}
```
