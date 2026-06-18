# Three Pointers (i + L + R)

## Definition

Three Pointers is a technique where one pointer (i) is fixed and two pointers (L and R) move toward each other. The array is usually sorted before applying this pattern.

This pattern is commonly used in triplet, quadruplet, and k-sum problems.

## When to Use

- 3Sum
- 4Sum
- Triplet Closest to Target
- k-Sum Problems
- Triplet Counting Problems

## Complexity

| Operation | Complexity |
|-----------|------------|
| Time | O(n²) |
| Space | O(1) |

## Brute Force vs Optimal

| Approach | Time | Space |
|-----------|------|-------|
| Brute Force | O(n³) | O(1) |
| Three Pointers | O(n²) | O(1) |

## Why Use Three Pointers?

Instead of checking every possible triplet, fix one element and use two pointers to find valid combinations, reducing the time complexity from O(n³) to O(n²).

## Problems Solved

### LC 15 - 3Sum

**Difficulty:** Medium

**Pattern:** Three Pointers (i + L + R)

## Approach

1. Sort the array.
2. Fix one element using pointer i.
3. Place L after i and R at the end.
4. Calculate the triplet sum.
5. Move pointers based on the sum.
6. Skip duplicate values.
7. Store valid triplets.

## Java Solution

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {

        Arrays.sort(nums);
        List<List<Integer>> res = new ArrayList<>();

        for (int i = 0; i < nums.length - 2; i++) {

            if (i > 0 && nums[i] == nums[i - 1]) continue;

            int L = i + 1;
            int R = nums.length - 1;

            while (L < R) {

                int sum = nums[i] + nums[L] + nums[R];

                if (sum == 0) {

                    res.add(Arrays.asList(nums[i], nums[L], nums[R]));

                    while (L < R && nums[L] == nums[L + 1]) L++;
                    while (L < R && nums[R] == nums[R - 1]) R--;

                    L++;
                    R--;

                } else if (sum < 0) {
                    L++;
                } else {
                    R--;
                }
            }
        }

        return res;
    }
}
