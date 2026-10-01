# Leetcode_Day61
# Day 61: Rearrange Array by Removing Distinct Values

**LeetCode Problem:** 4065. Rearrange Array by Removing Distinct Values
**Difficulty:** Easy
**Language:** Java
**Topic:** Arrays, Frequency Counting

## Problem Description

Given an integer array `nums`, start with an empty array `ans`. Repeatedly identify the distinct values remaining in `nums`, remove one occurrence of each value, and append those values to `ans` in ascending order. Continue until all elements are removed.

## Approach: Frequency Counting

1. Create a frequency array `freq` to count how many times each number appears.
2. Traverse `nums` and update the frequency of every element.
3. Create the result array `ans` with the same length as `nums`.
4. Repeatedly traverse the possible values in ascending order, from `0` to `100`.
5. If a value has a positive frequency, add it to `ans` and decrease its frequency by one.
6. Continue until all elements are added to the result array.

This approach ensures that distinct values are added in ascending order during each round.

## Java Solution

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int[] freq = new int[101];

        for (int i = 0; i < nums.length; i++) {
            freq[nums[i]]++;
        }

        int[] ans = new int[nums.length];
        int k = 0;

        while (k < nums.length) {
            for (int i = 0; i < 101; i++) {
                if (freq[i] > 0) {
                    ans[k] = i;
                    freq[i]--;
                    k++;
                }
            }
        }

        return ans;
    }
}
```

## Example

**Input**

```text
nums = [3,1,3,2,1,3]
```

**Output**

```text
[1,2,3,1,3,3]
```

**Explanation**

* Round 1: Distinct values are `1, 2, 3`.
* Round 2: Remaining values are `1, 3`.
* Round 3: Remaining value is `3`.

Combining the rounds gives `[1,2,3,1,3,3]`.

## Complexity Analysis

* **Time Complexity:** O(n + 101 × d), where `n` is the array length and `d` is the number of rounds. Since the value range is fixed, this is effectively O(n) for the given constraints.
* **Space Complexity:** O(n), for the result array and O(101) auxiliary space for frequency counting.

## What I Learned

* How to use a frequency array to count occurrences.
* How decreasing frequencies helps simulate removing elements.
* How traversing values in ascending order maintains the required ordering.
* How a simple counting technique can avoid repeatedly sorting the array.

## Key Takeaway

Sometimes, the simplest way to rearrange data is to count what you have and process it in the order you need.
