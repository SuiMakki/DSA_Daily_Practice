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
        // Frequency array to store the count of characters in the current window
        // Using 256 for all extended ASCII characters

        int[] count = new int[256]; 
        
        int l = 0; // Left pointer (start of window)
        int r = 0; // Right pointer (end of window)
        int maxLength = 0;

        while (r < s.length()) {
            char rightChar = s.charAt(r);
            count[rightChar]++;

            // If the current character count > 1, we have a duplicate.
            // Shrink the window from the left until the duplicate is removed.
            while (count[rightChar] > 1) {
                char leftChar = s.charAt(l);
                count[leftChar]--;
                l++;
            }

            // Update the maximum length found so far
            // Window size is (right - left + 1)
            maxLength = Math.max(maxLength, r - l + 1);
            
            // Expand the window
            r++;
        }

        return maxLength;
        }
        }


----------------------------------------

Key MetricsTime Complexity: O(n)
Space Complexity: O(1) (using a fixed 256-size array)
Pattern: Variable Size Sliding Window.
Data Structure: Frequency Array (Hash Map alternative)
