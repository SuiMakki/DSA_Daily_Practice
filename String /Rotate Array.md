Rotate Array
Solved 
Medium
Company Tags
You are given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

Example 1:

Input: nums = [1,2,3,4,5,6,7,8], k = 4

Output: [5,6,7,8,1,2,3,4]
Explanation:
rotate 1 steps to the right: [8,1,2,3,4,5,6,7]
rotate 2 steps to the right: [7,8,1,2,3,4,5,6]
rotate 3 steps to the right: [6,7,8,1,2,3,4,5]
rotate 4 steps to the right: [5,6,7,8,1,2,3,4]

Example 2:

Input: nums = [1000,2,4,-3], k = 2

Output: [4,-3,1000,2]
Explanation:
rotate 1 steps to the right: [-3,1000,2,4]
rotate 2 steps to the right: [4,-3,1000,2]

Constraints:

1 <= nums.length <= 100,000
-(2^31) <= nums[i] <= ((2^31)-1)
0 <= k <= 100,000
Follow up: Could you do it in-place with O(1) extra space?
-----------------------------------------------------------------

class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n;
        swap(nums, 0, n - 1);
        swap(nums, 0, k - 1);
        swap(nums, k, n - 1);
    }

    private void swap(int[] nums, int l, int r){
        while(l<r){
            int temp = nums[l];
            nums[l] = nums[r];
            nums[r] = temp;
            l++;
            r--;
        }
    }
}
------------------------------------------

Perfect — let’s do **k = 2** with:

```
nums = [1, 2, 3, 4]
```

We’ll go **step by step**.

---

## Initial

```
nums = [1, 2, 3, 4]
n = 4
k = 2 % 4 = 2
```

Goal: **rotate right by 2**

Expected result:

```
[3, 4, 1, 2]
```

---

## Step 1️⃣: Reverse entire array

```java
reverse(nums, 0, 3)
```

Before:

```
[1, 2, 3, 4]
```

After:

```
[4, 3, 2, 1]
```

---

## Step 2️⃣: Reverse first `k` elements

```java
reverse(nums, 0, 1)
```

Subarray:

```
[4, 3] → [3, 4]
```

Array now:

```
[3, 4, 2, 1]
```

---

## Step 3️⃣: Reverse remaining elements

```java
reverse(nums, 2, 3)
```

Subarray:

```
[2, 1] → [1, 2]
```

---

## ✅ Final Output

```
[3, 4, 1, 2]
```

---

## 🧠 One-line intuition

> Reverse all → reverse first `k` → reverse rest = rotate right by `k`.

If you want, I can also show:

* left rotation
* diagram with indices
* why this is O(1) space
