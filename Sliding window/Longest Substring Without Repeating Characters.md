Longest Substring Without Repeating Characters
Medium
Company Tags
Hints
Given a string s, find the length of the longest substring without duplicate characters.

A substring is a contiguous sequence of characters within a string.

Example 1:

Input: s = "zxyzxyz"

Output: 3
Explanation: The string "xyz" is the longest without duplicate characters.

Example 2:

Input: s = "xxxx"

Output: 1
Constraints:

0 <= s.length <= 1000
s may consist of printable ASCII characters.

--------------------------------------------------------


/**
 * Problem: Find the length of the longest substring without repeating characters.
 * Pattern: Sliding Window (Variable Size)
 * Time Complexity: O(n)
 * Space Complexity: O(k) where k is the size of the character set.
 */

        public class Solution {
            public int lengthOfLongestSubstring(String s) {
        // Convert string to char array to allow s[r] style access
        char[] str = s.toCharArray();
        int[] count = new int[256];
        
        int l = 0;
        int r = 0;
        int ans = 0;

        // Pattern: Sliding Window
        while (r < str.length) {
            // Expand window
            count[str[r]]++;

            // If duplicate found, shrink from left
            while (count[str[r]] > 1) {
                count[str[l]]--;
                l++;
            }

            // Update max length
            ans = Math.max(ans, r - l + 1);
            r++;
        }
        return ans;
           }
   


----------------------------------------

Key MetricsTime Complexity: O(n)
Space Complexity: O(1) (using a fixed 256-size array)
Pattern: Variable Size Sliding Window.
Data Structure: Frequency Array (Hash Map alternative)
