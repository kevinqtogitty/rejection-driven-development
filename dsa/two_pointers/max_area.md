# Max Area ![https://leetcode.com/problems/container-with-most-water/](LeetCode 11)

## Optimized 0(n)

```javascript
// nums is 1 INDEXED
function maxArea(walls) {
  // It's an array of walls with different walls
  // Find the indices of the two walls that hold the maximum amount of water
  // wall of the wall X distance between the walls, recompute every move and compare a max

  // 1. Two pointers - 1 on each right
  // 2. Compute the walls again and compare against the current max, set it if its greater
  // 3. Continue until loop condition breaks (left < right)

  // Edge cases
  // 1. [] -> 0
  // 2. [3] -> 0

  if (!walls.length || walls.length === 1) return 0 

  let left = 0, right = walls.length - 1
  let max = 0

  while (left < right) {
      const minWall = Math.min(walls[left], walls[right])
      const currArea = minWall * Math.abs(left - right)
      max = Math.max(max, currArea)

      if (walls[left] < walls[right]) {
          left++
      } else {
          right--
      }
  }

  return max
}
```
