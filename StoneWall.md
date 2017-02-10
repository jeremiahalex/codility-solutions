# [StoneWall](https://codility.com/programmers/lessons/7-stacks_and_queues/)
Cover "Manhattan skyline" using the minimum number of rectangles.

### Solution (JavaScript)
The illustration in this test, hints at the solution. We start at the height of the first block. When we encounter a new block, if it is shorter then we have to end our existing block, else we continue. If it is greter then we need to add another block. This can be achieved with a stack.

__[Test Score: 100%](https://codility.com/demo/results/trainingXCWPY8-T57/)__

```js
function solution(H) {
    let blocks = [H[0]]
    let count = 0
    for (let i = 1; i < H.length; ++i) {
        // is it taller, if so add a block to the stack
        if ( blocks.length === 0 || H[i] > blocks[blocks.length-1] ) {
            blocks.push(H[i])
            continue
        }
        
        //it is the same height, do nothing
        if ( H[i] === blocks[blocks.length-1] ) continue  
        
        // else it is shorter so pop a blocks until we get to the right height
        while ( H[i] < blocks[blocks.length-1] ) {
            blocks.pop()
            count++
        }
        if ( H[i] !== blocks[blocks.length-1] ) blocks.push(H[i])
    }
    
    return count + blocks.length
}
```
