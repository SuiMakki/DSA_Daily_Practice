          public class Solution {
              public int largestRectangleArea(int[] heights) {
                  int n = heights.length;
                  int maxArea = 0;
                  Stack<Integer> stack = new Stack<>();
          
                  for (int i = 0; i <= n; i++) {
                      while (!stack.isEmpty() &&
                           (i == n || heights[stack.peek()] >= heights[i])) {
                          int height = heights[stack.pop()];
                          int width = stack.isEmpty() ? i : i - stack.peek() - 1;
                          maxArea = Math.max(maxArea, height * width);
                      }
                      stack.push(i);
                  }
                  return maxArea;
              }
          }

----------------------------------------------------------------------------------------

Largest Rectangle In Histogram
Hard
Company Tags
Hints
You are given an array of integers heights where heights[i] represents the height of a bar. The width of each bar is 1.

Return the area of the largest rectangle that can be formed among the bars.

Note: This chart is known as a histogram.

Example 1:

Input: heights = [7,1,7,2,2,4]

Output: 8
Example 2:

Input: heights = [1,3,7]

Output: 7
Constraints:

1 <= heights.length <= 1000.
0 <= heights[i] <= 1000

-------------------------------------------------------------------------

Time & Space Complexity
Time complexity: 
O(n)
Space complexity: 
O(n)
