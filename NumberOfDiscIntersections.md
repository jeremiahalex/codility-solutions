# [NumberOfDiscIntersections](https://codility.com/programmers/lessons/6-sorting/)
Compute the number of intersections in a sequence of discs.

### Solution (JavaScript)
What we care about in this problem is the start and end points of each circle. Each time we encounter a new start, we gain x overlaps, where x is the number of current openings. Accordingly, we need a collection of the starts and ends in the order they occur.

__[Test Score: 100%](https://codility.com/demo/results/training9KRVZ9-GZJ/)__

```js
function solution(A) {
    const OPEN = 0
    const CLOSED = 1
    let points = []
    for (let i = 0; i < A.length; ++i){
        let start = i - A[i]    
        let end = i + A[i]   
        // prioritise openings first
        points.push({ i: start, type: OPEN})
        points.push({ i: end, type: CLOSED})
    }
    
    points.sort((a,b) => {
        if ( a.i > b.i ) return 1
        else if ( a.i < b.i ) return -1
        else {
            //if the position is the same then sort on type
            return a.type - b.type
        }
    })
    
    let count = 0
    let open = 0
    for (let i = 0; i < points.length; ++i){
        if (points[i].type === CLOSED){
            open--
        } else {
            count += open
            if ( count > 10000000 ) return -1
            open++
        }
    }
    
    return count
}
```
