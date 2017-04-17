# [Dominator](https://codility.com/programmers/lessons/8-leader/)
Find the index S such that the leaders of the sequences A[0], A[1], ..., A[S] and A[S + 1], A[S + 2], ..., A[N - 1] are the same.

### Solution (JavaScript)
The first step is to calculate the dominator, using hte same technique as the previous we can use a stack to remove the items in pairs, what is left is the candidate and if it occurs more than half it is a dominator. The second step is to then return an index of one of the occurances.

__[Test Score: 100%](https://codility.com/demo/results/trainingCDYYXS-RJF/)__

```js
function solution(A) {
    let dominator = null
    let stackSize = 0
    let dominatorIndex = -1
    A.forEach( (elem, index) => {
        if ( stackSize === 0 ) {
            dominator = elem
            dominatorIndex = index
            stackSize++
        } else if ( elem === dominator ) {
            // increase stack size as we have another indentical item
            stackSize++
        } else {
            // here we effectively discard this current element with the top from the stack
            stackSize--   
        }
    })
    
    let dominatorCount = A.reduce( (sum, cur) => {
        return dominator === cur ? ++sum : sum 
        }, 0 ) 
    
    if (dominatorCount <= A.length / 2) return -1
    
    return dominatorIndex
}

```
