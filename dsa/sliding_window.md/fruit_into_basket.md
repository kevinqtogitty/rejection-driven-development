# Fruit Into Basket ![https://leetcode.com/problems/fruit-into-baskets/](LeetCode 904)

## Solution O(n) — Space: O(1)

```javascript
function fruitIntoBasket(fruits) {
    const basket = new Map()
    let left = 0
    let max = 0

    for (let right = 0; right < fruits.length; right++) {
        // Add the fruit if it doesnt exist
        // else increment it
        if (!basket.has(fruits[right])) {
            basket.set(fruits[right], 1)
        } else {
            basket.set(fruits[right], basket.get(fruits[right]) + 1)
        }

        // When there's 3 fruits in the basket, it means right is looking
        // at a 3rd new fruit and left is looking at the first unique fruit
        while(basket.size > 2) {
            basket.set(fruits[left], basket.get(fruits[left]) - 1)
            if (basket.get(fruits[left]) === 0) {
                basket.delete(fruits[left])
            }

            left++
        }

        max = Math.max(max, right - left + 1)
    }

    return max
};
```
