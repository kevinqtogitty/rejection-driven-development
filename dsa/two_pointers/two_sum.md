# Two Sum ![https://leetcode.com/problems/two-sum/](LeetCode 1)

## Brute Force 0(n^2)

```javascript
function twoSum(nums, target) {
  // Two loops, search every possible combination
  for (const [ i, currValue ] of nums.entries()) {
      for (const j of nums) {
          const normalizedIndex = j + 1
          if ( currValue +  nums[normalizedIndex] === target) return [i, normalizedIndex]
      }
  }
}
```

## Optimized 0(n)

```javascript
function twoSum(nums, target) {
  // Keep track of seen values in a map
  // { value: index }
  // If the missing value is in the lookup table, return the pair
  // Else store the current value in the lookup table for future iterations
    const seen = {}

    for (const [ i, curr ] of nums.entries()) {
        const missing = target - curr
        const lookup = seen[missing]

        if (lookup || lookup === 0) {
            return [ i, lookup]
        }

        seen[curr] = i
    }
    return []
}
```
