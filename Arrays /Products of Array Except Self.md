Products of Array Except Self

<img width="1261" height="699" alt="image" src="https://github.com/user-attachments/assets/0b4869f3-7edf-4644-9c1a-8245bebdc40b" />

Products of Array Except Self
Given an integer array nums, return an array output where output[i] is the product of all the elements of nums except nums[i].

Each product is guaranteed to fit in a 32-bit integer.

Follow-up: Could you solve it in 
O(n)
O(n) time without using the division operation?

Example 1:

Input: nums = [1,2,4,6]

Output: [48,24,12,8]
Example 2:

Input: nums = [-1,0,1,2,3]

Output: [0,-6,0,0,0]
Constraints:

2 <= nums.length <= 1000
-20 <= nums[i] <= 20
-------------------------------------------------------

<img width="1269" height="714" alt="image" src="https://github.com/user-attachments/assets/6312b3a4-3efd-4128-8833-8866e915a969" />

package leetcode.medium;

/**
 * Created by nikoo28 on 7/12/19 1:23 AM
 */

class ProductOfArrayExceptSelf {

  public int[] productExceptSelf(int[] nums) {

    // Array to store all left multiplication
    int[] left = new int[nums.length];

    // Array to store all right multiplication
    int[] right = new int[nums.length];

    left[0] = 1;
    for (int i = 1; i < nums.length; i++) {
      left[i] = left[i - 1] * nums[i - 1];
    }

    right[nums.length - 1] = 1;
    for (int i = nums.length - 2; i > -1; i--) {
      right[i] = right[i + 1] * nums[i + 1];
    }

    int[] ans = new int[nums.length];
    for (int i = 0; i < nums.length; i++) {
      ans[i] = left[i] * right[i];
    }

    return ans;
  }

}
