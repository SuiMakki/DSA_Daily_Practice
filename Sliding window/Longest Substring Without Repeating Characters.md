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

        class Solution {
            public int lengthOfLongestSubstring(String s) {
        // Convert to char array to use s[r] syntax like in the image
        char[] str = s.toCharArray();
        
        int[] count = new int[256];
        int l = 0;   // starting index of window
        int r = 0;   // ending index of window
        int ans = 0; // length of longest substring no repeating characters

        while (r < str.length) {
            
            count[str[r]]++;

            while (count[str[r]] > 1) {
                count[str[l]]--;
                l++;
            }

            ans = Math.max(ans, r - l + 1);
            r++;
        }
        
        return ans;
    }
        }
----------------------------------------

Key MetricsTime Complexity: O(n)
Space Complexity: O(1) (using a fixed 256-size array)
Pattern: Variable Size Sliding Window.
Data Structure: Frequency Array (Hash Map alternative)
