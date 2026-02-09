# Longest Repeating Character Replacement![https://leetcode.com/problems/longest-repeating-character-replacement/description/](LeetCode 424)

## Solution O(n) — Space: O(1)

```javascript
function characterReplacement(s, k) {
    // expand the window and track frquencies
    // all we need to do to determine that our window is invalid
    // is (right - left + 1) - most occuring char > k

    let frequencies = {}
    let mostOccuring = 0
    let left = 0
    let maxLengthSubString = 0

    for (let right = 0; right < s.length; right++) {
        const char = s[right]
        frequencies[char] = (frequencies[char] || 0) + 1
        mostOccuring = Math.max(mostOccuring, frequencies[char])

        // If the most occuring character minus the current substring length
        // is greater than k flips, then we know the current window
        // is invalid. So we need to keep moving left up until the new substring
        // contains less than the number of allowed flips
        while ((right - left + 1) - mostOccuring > k) {
            frequencies[s[left]]--
            left++
        }

        maxLengthSubString = Math.max(maxLengthSubString, right - left + 1)
    }

    return maxLengthSubString
};
;
```
