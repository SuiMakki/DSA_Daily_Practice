Decode String
Solved 
Medium
Company Tags
You are given an encoded string s, return its decoded string.

The encoding rule is: k[encoded_string], where the encoded_string inside the square brackets is being repeated exactly k times. Note that k is guaranteed to be a positive integer.

You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. There will not be input like 3a, 2[4], a[a] or a[2].

The test cases are generated so that the length of the output will never exceed 100,000.

Example 1:

Input: s = "2[a3[b]]c"

Output: "abbbabbbc"
Example 2:

Input: s = "axb3[z]4[c]"

Output: "axbzzzcccc"
Example 3:

Input: s = "ab2[c]3[d]1[x]"

Output: "abccdddx"
Constraints:

1 <= s.length <= 30
s is made up of lowercase English letters, digits, and square brackets '[]'.

All the integers in s are in the range [1, 300].
s is guaranteed to be a valid input.


-------------------------------------------------------------------------------

    import java.util.Stack;
    
    class Solution {
        public String decodeString(String s) {
            Stack<Object> stack = new Stack<>(); 
            int curNum = 0; 
            String curString = "";
    
            for (int i = 0; i < s.length(); i++) {
                char c = s.charAt(i);
    
                if (c == '[') {
                    stack.push(curString);
                    stack.push(curNum);
                    curString = "";
                    curNum = 0;
                } else if (c == ']') {
                    int num = (int) stack.pop();
                    String prevString = (String) stack.pop();
                    
                    // Mirroring Python's: num * curString
                    String repeated = "";
                    for (int j = 0; j < num; j++) {
                        repeated += curString;
                    }
                    curString = prevString + repeated;
                } else if (Character.isDigit(c)) {
                    curNum = curNum * 10 + (c - '0');
                } else {
                    curString += c;
                }
            }
            return curString;
        }
    }
-------------------------------------------------------------------------------

O(n) - time n space
