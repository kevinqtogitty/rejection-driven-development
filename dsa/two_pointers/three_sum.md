# 3Sum ![https://leetcode.com/problems/3sum/description/](LeetCode 15)

## Solution O(n^2) — Space: O(1) (excluding sort and output)

```javascript
function threeSum(nums) {
  // Criteria
  // 1. Triplets must sum to 0
  // 2. Triplets Must be all unique indices
  // 3. Can be multiple triplets, a value can be a part os multiple triplets

  // Steps:
  // 1. sort
  // 2. initialize empty array as return value
  // 3. for loop over nums
  //  3A. If the current indexs' value is > 0 break the loop
  //  3B. If the current index is greater than zero AND the current value is the same as the 
  //      previous value, skip to the next iteration
  // 4. Initialize start and end pointers, start begine at the i + 1 index, end always starts
  //    at the same place, the end
  // 5. Start the squezing of the start and end pointers
  // 5. Compute the sum
  // 6. If sum === 0
  //  6A. Push the triplet into our return value
  //  6B. While start < end, and start pointer does not equal the previous value, then increment
  //  6C. While start < end, and end pointer does not equal the previous value, then decrement
  // 7. Else if sum < 0, icrement start pointer
  // 8. Else this means sum > 0, decrement end pointer
  // 9. return return value after the loop

    nums.sort((a, b) => a - b)
    const triplets = []

    // [-1, -1, 0, 1, 2, 3]
    //   ^   ^ squeezee  ^
    //   i   start       end

    for (const [ i, currValue ] of nums.entries()) {
        if (currValue > 0) break
        if (i > 0 && currValue === nums[i - 1]) continue

        let start = i + 1, end = nums.length - 1

        while (start < end) {
            const sum = currValue + nums[start] + nums[end]
            if (sum === 0) {
                triplets.push([currValue, nums[start], nums[end]])
                start++, end-- // squeeze the friggin window
                while(start < end && nums[start] === nums[start - 1]) {
                    start++ // if the previous start value is the same keep bumpin'
                }
                while(start < end && nums[end] === nums[end + 1]) {
                    end-- // if the previous end value is the same keep bumpin'
                }
            } else if (sum < 0) {
                start++
            } else {
                end--
            }
        }
    }
  return triplets
}
```
