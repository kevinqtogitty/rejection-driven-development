# Move Zeroes ![https://leetcode.com/problems/move-zeroes/](LeetCode 11)

## Solution O(n) — Space: O(1)

```javascript
function moveZeroes(walls) {
  // This is technically a fast and slow pointer technique
  // We need to swap the values in place, in JS we can achieve this with some
  // syntactic sugar using array desstructuring i.e.
  // 
  // [ left, right ] = [ right, left ]
  // 
  // This is essentially instancing a temp var and swapping values between
  // 3 variables
  // 
  // The idea here is you left pointer stays on zeros, when your right pointer
  // encounters a non-zero number, you swap the values at those indexs
  // **remember you are not swapping the position of the pointers, just the values

    let left = 0;
    let right = 0;
    while (right < nums.length) {
      // if we encounter a 0 left pointer stays behind and doesnt get incrmeneted
      // so when right finds the next non-zero, we swap the values and increment
      // left
      // 
      // if the input is all non-zeroes, then left and right just track each other
      // and swap the value with itself in place
        if (nums[right] !== 0) {
            [nums[left], nums[right]] = [nums[right], nums[left]];
            left++;
        }
        right++;
    }
```
