# Two Pointers on Two Arrays

## Definition

Two Pointers on Two Arrays is a technique where one pointer is used for each array. Both arrays are traversed simultaneously, and pointers move based on comparison results.

This pattern is commonly used in intersection, union, merge, and string matching problems.

## When to Use

- Intersection of Two Arrays
- Union of Arrays
- Merge Sorted Arrays
- Backspace String Compare
- String Matching Problems

## Complexity

| Operation | Complexity |
|------------|------------|
| Time | O(n + m) |
| Space | O(1) / O(n + m) |

## Brute Force vs Optimal

| Approach | Time | Space |
|-----------|------|-------|
| Brute Force | O(n × m) | O(1) |
| Two Pointers | O(n + m) | O(1) |

## Why Use Two Pointers on Two Arrays?

Instead of comparing every element of one array with every element of another array, both arrays are traversed together, reducing the time complexity from O(n × m) to O(n + m).

---

## Problems Solved

### LC 349 - Intersection of Two Arrays

**Difficulty:** Easy

**Pattern:** Two Pointers on Two Arrays

## Approach

1. Sort both arrays.
2. Use one pointer for each array.
3. Compare current elements.
4. Move the pointer with the smaller value.
5. If elements are equal, add them to the result.
6. Skip duplicate values and continue traversal.

## Java Solution

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {

        Arrays.sort(nums1);
        Arrays.sort(nums2);

        List<Integer> result = new ArrayList<>();

        int i = 0, j = 0;

        while (i < nums1.length && j < nums2.length) {

            if (nums1[i] < nums2[j]) {
                i++;
            } else if (nums1[i] > nums2[j]) {
                j++;
            } else {

                result.add(nums1[i]);

                i++;
                j++;

                while (i < nums1.length && nums1[i] == nums1[i - 1]) {
                    i++;
                }

                while (j < nums2.length && nums2[j] == nums2[j - 1]) {
                    j++;
                }
            }
        }

        return result.stream().mapToInt(Integer::intValue).toArray();
    }
}
