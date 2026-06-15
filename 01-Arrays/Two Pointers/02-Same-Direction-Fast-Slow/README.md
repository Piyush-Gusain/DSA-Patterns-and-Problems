# Same Direction Fast + Slow

## Definition

Same Direction Fast + Slow is a Two Pointers technique where both pointers move in the same direction. The slow pointer tracks valid elements, while the fast pointer scans the array.

This pattern is commonly used for in-place array modification, duplicate removal, and element shifting problems.

## When to Use

- Remove Duplicates from Sorted Array
- Move Zeroes
- Remove Element
- In-Place Array Modification
- Data Compression Problems

## Complexity

| Operation | Complexity |
|-----------|------------|
| Time | O(n) |
| Space | O(1) |

## Brute Force vs Optimal

| Approach | Time | Space |
|-----------|------|--------|
| Brute Force | O(n²) | O(1) |
| Fast + Slow Pointers | O(n) | O(1) |

## Why Use Fast + Slow Pointers?

Instead of repeatedly shifting elements or checking duplicates multiple times, the fast pointer scans the array while the slow pointer maintains the correct position, reducing unnecessary operations and achieving O(n) time complexity.

## Problems Solved

### LC 26 - Remove Duplicates from Sorted Array

**Difficulty:** Easy

**Pattern:** Same Direction Fast + Slow

### Approach

1. Place slow pointer at the first element.
2. Use fast pointer to scan the array.
3. When a new unique element is found, move slow forward.
4. Copy the unique element to the slow position.
5. The final length is slow + 1.

### Java Solution

```java
class Solution {
    public int removeDuplicates(int[] nums) {

        int slow = 0;

        for (int fast = 1; fast < nums.length; fast++) {

            if (nums[fast] != nums[slow]) {
                slow++;
                nums[slow] = nums[fast];
            }
        }

        return slow + 1;
    }
}
```
