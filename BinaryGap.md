# [BinaryGap](https://codility.com/programmers/lessons/1-iterations/)
Find longest sequence of zeros in binary representation of an integer.

__[Test Score: 100%](https://codility.com/demo/results/trainingJ2Y5ZT-6QZ/)__

### Solution (JavaScript)
```js
function solution(N) {
    // first step is to convert the number to it's binary representation - we know it is positive, so can just use the toString method
    let binary = N.toString(2)

    // next we want to keep track of the longest gap we find and also the size of the current
    var longest = 0
    var current = -1 // -1 to indicate no current gap
    for (let i = 0; i < binary.length; ++i){
        // two cases, we encounter a 1 or a 0
        // we can using == so that character is auto-converted to int for us in comparison
        if (binary[i] == 1){
            // if a 1 then we are either terminating (current > 0) a sequence or starting one
            if (current > longest) {
                // if terminating then we set our new maximum
                longest = current
                // we can also terminate early, if it is not possible to encounter a longer sequence
                if (longest > binary.length - i ) break
            }
            // set current to zero to start a new sequence
            current = 0
        } else if (current >= 0) {
            // if we encounter a zero and have a current sequence then increment the counter
            current++
        }
    }

    return longest
}
```
