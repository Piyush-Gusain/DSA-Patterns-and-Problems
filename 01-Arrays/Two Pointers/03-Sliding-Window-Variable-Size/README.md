# Sliding Window (Variable Size)

## Definition

Sliding Window (Variable Size) is a Two Pointers technique where both left and right pointers move forward. The window expands when the condition is valid and shrinks when the condition becomes invalid.

This pattern is commonly used in subarray and substring problems where we need to find the longest, shortest, maximum, or minimum valid window.

## When to Use

- Longest Substring Problems
- Shortest Subarray Problems
- Subarray Sum Conditions
- Frequency-Based Problems
- Dynamic Window Constraints

## Complexity

| Operation | Complexity |
|-----------|------------|
| Time | O(n) |
| Space | O(k) |

*k = Window Size / HashMap Size*

## Brute Force vs Optimal

| Approach | Time | Space |
|-----------|------|--------|
| Brute Force | O(n²) | O(1) |
| Sliding Window | O(n) | O(k) |

## Why Use Sliding Window?

Instead of generating and checking every possible subarray or substring, the window expands and shrinks dynamically, allowing each element to be processed at most twice and reducing the time complexity from O(n²) to O(n).

## Problems Solved

### LC 3 - Longest Substring Without Repeating Characters

**Difficulty:** Medium

**Pattern:** Sliding Window (Variable Size)

### Approach

1. Expand the window using the right pointer.
2. Store character frequencies in a HashMap.
3. If a duplicate character appears, shrink the window from the left.
4. Maintain the maximum valid window length.
5. Return the longest substring length.

### Java Solution

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {

        int left = 0;
        int maxLen = 0;

        HashMap<Character, Integer> map = new HashMap<>();

        for (int right = 0; right < s.length(); right++) {

            char c = s.charAt(right);
            map.put(c, map.getOrDefault(c, 0) + 1);

            while (map.get(c) > 1) {
                char leftChar = s.charAt(left);
                map.put(leftChar, map.get(leftChar) - 1);
                left++;
            }

            maxLen = Math.max(maxLen, right - left + 1);
        }

        return maxLen;
    }
}
```
