
# Valid Triangs ![https://leetcode.com/problems/valid-triangle-number/description/](LeetCode 611)

## Optimized — Time: O(n^2), Space: O(1) (excluding sort)

```javascript
function validTriangles(nums) {
  // If we sort from lowest to highest this is just a 3sum problem where the
  // left and right pointers are on the right side
  // 
  // stop the for loop when is at index 1 beause a triganle has three sides so
  // the last iteration when i is at index two looks like [2,2,3....]
  //                                                       l r i
  // 
  // compute the left and right and check if its greater than i
  // if so thats a valid triangle
  let found = 0
  nums.sort((low, high) => low - high)
  
  for(let i = nums.length - 1; i >= 2; i--) {
      let left = 0, right = i - 1

      while(left < right) {
          if (nums[left] + nums[right] > nums[i]) {
              // if the current left and right sum make to be greater than the longest side
              // that means everything in between left and right is also valid
              found += right - left
              right--
          } else {
              // if left + right < nums[i] we need to bump the left pointer up to the next
              // largest value
              left++
          }
      }
  }
  
  return found
}
```
