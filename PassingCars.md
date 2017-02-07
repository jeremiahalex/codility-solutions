# [PassingCars](https://codility.com/programmers/lessons/5-prefix_sums/)
Count the number of passing cars on the road.

### Solution (JavaScript)
In this challenge we can keep track of the number of cars travelling east, then every time we pass a car travelling west we know that each car going east will make another pairs.

__[Test Score: 100%](https://codility.com/demo/results/training7NHYFC-HSX/)__

```js
function solution(A) {
    let east = 0
    let pairs = 0
    
    for (let i = 0; i < A.length; ++i) {
        if (A[i] === 0) east++
        else {
            pairs += east
            // if we exceed the passing car count then return
            if (pairs > 1000000000) return -1
        }
    }
    
    return pairs
}
```
