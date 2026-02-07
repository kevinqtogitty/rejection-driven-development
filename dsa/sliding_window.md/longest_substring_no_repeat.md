# Long Substring Without Repeating Characters [https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](LeetCode 3)

## Solution O(n) — Space: O(1)

```javascript
function lengthOfLongestSubstring(s) {
    let left = 0, right = 0, max = 0, seen = new Set()
    // You can also use a outer for loop and instance the right pointer there
    while (right < s.length) {
      // If this is true, that means that right is currently looking at a duplicate
      // BUT not yet in the set. BOTH LEFT AN RIGHT RIGHT ARE LOOKING AT THE SAME CHAR i.e
      // [ a, b, c, a]
      //   l        r 
      // This means we've reached the current maximum contigous uniquee substring
      // we need to start over and move left up to right, start a new substring
        while(seen.has(s[right])) {
            seen.delete(s[left])
            left++
        }
      // essentially repeat this process, expand until we find a duplicate
      // or reach the end, every iteration checking the max
        seen.add(s[right])
      // when we slide check the new max
        max = Math.max(max, right - left + 1)
        right++
    }

    return max
};
```
