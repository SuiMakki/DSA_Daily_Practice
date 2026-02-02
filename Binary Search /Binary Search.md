Binary Search
Easy
Company Tags
Hints
You are given an array of distinct integers nums, sorted in ascending order, and an integer target.

Implement a function to search for target within nums. If it exists, then return its index, otherwise, return -1.

Your solution must run in 
O(logn) time.

Example 1:

Input: nums = [-1,0,2,4,6,8], target = 4

Output: 3
Example 2:

Input: nums = [-1,0,2,4,6,8], target = 3

Output: -1
Constraints:

1 <= nums.length <= 10000.
-10000 < nums[i], target < 10000
All the integers in nums are unique.

---------------------------------------------------------------------------------

      class Solution {
          public int search(int[] nums, int target) {
              int l = 0, r = nums.length;
      
              while(l <= r){
                  int m = l + ((r - l)/2);
                  if(nums[m] > target){
                      r = m - 1;
                  }else if(nums[m] < target){
                      l = m + 1;
                  }else{
                      return m;
                  }
              }
              return -1;
          }
      }


-----------------------------------------------------------------------

Time & Space Complexity
Time complexity: 
O(logn)
Space complexity: 
O(1)
