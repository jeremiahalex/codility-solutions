# [EquiLeader](https://codility.com/programmers/lessons/8-leader/)
Find the index S such that the leaders of the sequences A[0], A[1], ..., A[S] and A[S + 1], A[S + 2], ..., A[N - 1] are the same.

### Solution (JavaScript)
We can reason that to split the array and have two identical leaders, it must be the same leader for the whole array - so our first step is to calculate that leader. This has two steps, first we decide a candiate for the leader (ie. the number that occurs most often) and then we count the number of occurances to see if it is more than half. To find the candidate we can sort and pick the middle number or we can repeatedly remove pairs of unmatched numbers, whatever is left is the most frequently occuring number, we can do this using a stack. To find the equi leader we can again loop through the array but this time, using the index as the pivot, we compare the number of leaders each side of it, increasing our equi leader count if the correct conditions are met

__[Test Score: 100%](https://codility.com/demo/results/training5W3HNR-5UT/)__

```js
function solution(A) {
    let leader = null
    let stackSize = 0

    for (let i = 0; i < A.length; ++i) {
        if (stackSize === 0) {
            // empty stack store the value
            leader = A[i]
            stackSize++
        } else {
            // compare the value against that in the stack and add if same or decrease if different
            if (A[i] === leader) {
                stackSize++       
            } else {
                stackSize--   
            }
        }
    }
    
    // we need a count of leaders
    let leaderCount = A.reduce((sum,elem) => {
        return elem === leader ? sum + 1 : sum
        }, 0 ) 
    
    // do we have a leader? if not then no need to continue
    if ( leaderCount <= A.length / 2 ) return 0
    
    let equiLeaders = 0
    let leaderOccurances = 0
    for (let s = 0; s < A.length; ++s) {
        if (A[s] === leader) {
          leaderOccurances++
        }
        let remainingLeaders = leaderCount - leaderOccurances
        let leftLength = s + 1
        let rightLength = A.length - leftLength
          
        if ( leaderOccurances > leftLength/2 && remainingLeaders > rightLength/2 ) {
            equiLeaders++
        }
    }
    
    return equiLeaders
}
```
