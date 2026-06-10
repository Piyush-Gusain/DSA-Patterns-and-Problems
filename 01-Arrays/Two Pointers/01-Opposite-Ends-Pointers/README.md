# Opposite Ends Pointers

## Definition

Opposite Ends Pointers is a Two Pointers technique where one pointer starts from the beginning of the array and the other starts from the end. Both pointers move toward each other based on a condition.

This pattern is commonly used in sorted arrays, palindrome checking, pair-sum problems, and partitioning problems.

---

## When to Use

- Sorted Array Pair Sum
- Palindrome Problems
- Container Problems
- 3Sum / 4Sum
- Array Partitioning

---

## Complexity

| Operation | Complexity |
|------------|------------|
| Time | O(n) |
| Space | O(1) |

---

## Brute Force vs Optimal

| Approach | Time | Space |
|-----------|------|--------|
| Brute Force | O(n²) | O(1) |
| Opposite Ends Pointers | O(n) | O(1) |

### Why Use Opposite Ends Pointers?

Instead of checking every possible pair, two pointers move toward each other and process each element at most once, reducing the time complexity from **O(n²)** to **O(n)**.

---
## Problems Solved

### LC 167 - Two Sum II

**Difficulty:** Easy

**Pattern:** Opposite Ends Pointers

#### Approach

- Place one pointer at the beginning.
- Place another pointer at the end.
- Compare sum with target.
- Move left pointer if sum is smaller.
- Move right pointer if sum is larger.

#### Java Solution

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {

        int left = 0;
        int right = numbers.length - 1;

        while(left < right) {

            int sum = numbers[left] + numbers[right];

            if(sum == target) {
                return new int[]{left + 1, right + 1};
            } else if (sum < target) {
                left++;
            } else {
                right--;
            }
        }

        return new int[]{-1,-1};
    }
}
