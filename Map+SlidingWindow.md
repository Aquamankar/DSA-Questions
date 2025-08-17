# 🚀 HashMap + Sliding Window Interview Questions

This document covers common **HashMap + Sliding Window** coding problems
frequently asked in interviews.

They are typically asked in **string** and **array** manipulation
problems.

------------------------------------------------------------------------

## 🔑 Core Pattern

1.  Use **two pointers** (`left`, `right`) to represent the sliding
    window.\
2.  Use a **HashMap/HashSet** to store:
    -   Character → frequency
    -   Or Character → last index\
3.  Expand window (`right++`) until condition breaks.\
4.  Shrink window (`left++`) until condition is satisfied again.

------------------------------------------------------------------------

## 📘 Problems

### 1. Longest Substring Without Repeating Characters

-   **Problem**: Find length of the longest substring without repeating
    characters.\
-   **Example**: `abcabcbb → 3 ("abc")`\
-   **Approach**: HashMap to store last index of character. Move `left`
    pointer when duplicate found.

------------------------------------------------------------------------

### 2. Contains Duplicate II

-   **Problem**: Check if there are duplicate elements within distance
    `k`.\
-   **Example**: `nums = [1,2,3,1], k=3 → true`\
-   **Approach**: Sliding window of size `k` with HashSet/HashMap.

------------------------------------------------------------------------

### 3. Find All Anagrams in a String

-   **Problem**: Find all start indices of `p`'s anagrams in `s`.\
-   **Example**: `s="cbaebabacd", p="abc" → [0,6]`\
-   **Approach**: Sliding window of length `p.length()`. Compare
    frequency maps.

------------------------------------------------------------------------

### 4. Minimum Window Substring

-   **Problem**: Find the smallest substring of `s` containing all
    characters of `t`.\
-   **Example**: `s="ADOBECODEBANC", t="ABC" → "BANC"`\
-   **Approach**: Expand window with `right`, shrink with `left` until
    valid. Track min length.

------------------------------------------------------------------------

### 5. Longest Substring with At Most K Distinct Characters

-   **Problem**: Find the longest substring containing at most `k`
    distinct characters.\
-   **Example**: `"eceba", k=2 → 3 ("ece")`\
-   **Approach**: HashMap stores char frequency. Shrink when distinct \>
    k.

------------------------------------------------------------------------

### 6. Longest Substring with At Most Two Distinct Characters

-   **Special Case**: Same as above with `k=2`.\
-   **Example**: `"ccaabbb" → 5 ("aabbb")`.

------------------------------------------------------------------------

### 7. Longest Repeating Character Replacement

-   **Problem**: Replace at most `k` chars to make substring have same
    char.\
-   **Example**: `"AABABBA", k=1 → 4 ("AABA")`.\
-   **Approach**: Track max frequency char in window. Shrink if
    `(window - maxFreq) > k`.

------------------------------------------------------------------------

### 8. Subarrays with K Different Integers

-   **Problem**: Count subarrays with exactly `k` different integers.\
-   **Example**: `[1,2,1,2,3], k=2 → 7`.\
-   **Approach**: Count(atMostK) - Count(atMostK-1) using sliding
    window.

------------------------------------------------------------------------

### 9. Smallest Subarray with Sum ≥ K

-   **Problem**: Find smallest subarray length with sum ≥ k.\
-   **Example**: `[2,3,1,2,4,3], k=7 → 2 ([4,3])`.\
-   **Approach**: Sliding window with running sum.

------------------------------------------------------------------------

### 10. Subarray Sum Equals K

-   **Problem**: Count number of subarrays that sum to `k`.\
-   **Example**: `[1,2,3], k=3 → 2`.\
-   **Approach**: Prefix sum + HashMap.

------------------------------------------------------------------------

### 11. Permutation in String

-   **Problem**: Check if `s2` contains a permutation of `s1`.\
-   **Example**: `s1="ab", s2="eidbaooo" → true`.\
-   **Approach**: Sliding window of `s1.length()`. Compare frequency
    maps.

------------------------------------------------------------------------

## 🧩 Common Templates

### Sliding Window Template (Strings)

``` java
int left = 0;
Map<Character, Integer> map = new HashMap<>();

for (int right = 0; right < s.length(); right++) {
    char c = s.charAt(right);
    map.put(c, map.getOrDefault(c, 0) + 1);

    while (/* condition breaks */) {
        char leftChar = s.charAt(left);
        map.put(leftChar, map.get(leftChar) - 1);
        if (map.get(leftChar) == 0) map.remove(leftChar);
        left++;
    }

    // update answer
}
```

### Sliding Window Template (Arrays)

``` java
int left = 0, sum = 0;

for (int right = 0; right < nums.length; right++) {
    sum += nums[right];

    while (sum >= target) {
        // update answer
        sum -= nums[left];
        left++;
    }
}
```

------------------------------------------------------------------------

## 📌 Tips

-   Always ask: **"Do I need substring length, indices, or the substring
    itself?"**\
-   Use **HashMap\<Character, Integer\>** for counts.\
-   For **exact `k` distinct** problems → use
    `atMost(k) - atMost(k-1)`.\
-   For **replacement problems** → track `maxFreq` inside window.
