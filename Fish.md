# [Fish](https://codility.com/programmers/lessons/7-stacks_and_queues/)
N voracious fish are moving along a river. Calculate how many fish are alive.

### Solution (JavaScript)
To solve this in N time, we need to loop through the array once. So whilst doing that, we need to track what we have encountered. If we encounter a 1 (downstream fish) then we can push it onto a stack for downstream fish, if we encounter a 0 we know it will encounter all the fish on the downstream stack, so we loop through and compare against each, either killing a downstream fish or the upstream fish until either the upstream fish is dead or all of the downstream fish are.

__[Test Score: 100%](https://codility.com/demo/results/training9MJ2YG-GJ5/)__

```js
function solution(A, B) {
    let downstream = []
    let upstream = []
    for (let i = 0; i < A.length; ++i) {
        if (B[i] === 1) {
            downstream.push(A[i])
        } else {
            let upstreamfish = A[i]
            while ( downstream.length > 0 ) {
                let downstreamFish = downstream[downstream.length-1]
                if (downstreamFish > upstreamfish) {
                    upstreamfish = null
                    break
                } else {
                    downstream.pop()
                }
            }
            if ( upstreamfish !== null ) {
                upstream.push(upstreamfish)
            }
        }
    }
    return downstream.length + upstream.length
}
```
