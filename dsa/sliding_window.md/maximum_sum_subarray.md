# Maximum Subarray [https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](LeetCode 53)

## Solution O(n) — Space: O(1)

The most common solution here is Kadans Algorithm, not really sliding window.
Instead of keeping a window, you keep a tracking sum as you move. If your
tracking sum is less than 0, well you might as well just set it to zero
thus effectivly starting a new 'window'

```javascript
function maxSubArray(s) {
  // you need to use kadanes algorithm
  // you dont need to track a window
  // just need to keep track of a minium value
  // the issue is negative numbers
  // if you see a negative number and add it to you tracking sum
  // and it makes it negative, you're beter off just starting at 0 again

  /**
      max 6
      tracking sum = 3
      [ -2, 1, -3, 4, -1, 2, 1, -5, 4 ]
                                    l   
   */

   let maxSum = -Infinity
   let trackingSum = 0

   for (const num of nums) {
      currSum += num
      maxSum = Math.max(trackingSum, maxSum)

      if (trackingSum < 0) trackingSum = 0
   }

   return maxSum
};
```
