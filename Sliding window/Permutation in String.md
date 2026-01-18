Permutation in String
Medium
Company Tags
Hints
You are given two strings s1 and s2.

Return true if s2 contains a permutation of s1, or false otherwise. That means if a permutation of s1 exists as a substring of s2, then return true.

Both strings only contain lowercase letters.

Example 1:

Input: s1 = "abc", s2 = "lecabee"

Output: true
Explanation: The substring "cab" is a permutation of "abc" and is present in "lecabee".

Example 2:

Input: s1 = "abc", s2 = "lecaabee"

Output: false
Constraints:

1 <= s1.length, s2.length <= 1000

------------------------------------------------------

    class Solution {
    public boolean checkInclusion(String s1, String s2) {
        int[] map = new int[26];
        for (char c : s1.toCharArray()) map[c - 'a']++;

        int i = 0, j = 0, totalChars = s1.length();

        while (j < s2.length()) {
            if (map[s2.charAt(j++) - 'a']-- > 0) totalChars--;

            if (totalChars == 0) return true;

            if (j - i == s1.length() && map[s2.charAt(i++) - 'a']++ >= 0) {
                totalChars++;
            }
        }
        return false;
    }
    }

-----------------------------------------------------

Pattern: Fixed-Size Sliding Window
Time Complexity: $O(n)
Why? We visit each character in s2 exactly once.
Space Complexity: $O(1)
Why? The frequency array size is always 26, regardless of input length.

Permutation in String: Window size is Fixed. You look for a specific set of characters.
