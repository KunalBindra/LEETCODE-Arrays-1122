# LEETCODE-Arrays-1122
Let's go through a dry run of the given code. We'll use an example to better understand how it works.

### Example
- `arr1 = [2, 3, 1, 3, 2, 4, 6, 7, 9, 2, 19]`
- `arr2 = [2, 1, 4, 3, 9, 6]`

### Steps

1. **Initialization**
   - `ans` array of length equal to `arr1` initialized to zero: `ans = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]`
   - `count` array of size 1001 initialized to zero: `count = [0, 0, 0, ..., 0]` (1001 zeros)
   - `i` is initialized to `0`.

2. **Count occurrences in `arr1`**
   - For each element `a` in `arr1`, increment the count of `a` in the `count` array.
     ```
     arr1 = [2, 3, 1, 3, 2, 4, 6, 7, 9, 2, 19]
     After counting, count array will look like:
     count = [0, 1, 3, 2, 1, 0, 1, 1, 0, 1, ..., 1, 0, ..., 0] (1001 elements)
     Indexes 1, 2, 3, 4, 6, 7, 9, 19 have values 1, 3, 2, 1, 1, 1, 1, 1 respectively.
     ```

3. **Fill `ans` array based on `arr2`**
   - For each element `a` in `arr2`, place `a` in `ans` according to the count in `count`.
     ```
     arr2 = [2, 1, 4, 3, 9, 6]
     After processing arr2:
     ans = [2, 2, 2, 1, 4, 3, 3, 9, 6, 0, 0]
     Explanation:
     - 2 appears 3 times in count: [2, 2, 2, ..., 0]
     - 1 appears 1 time in count: [2, 2, 2, 1, ...]
     - 4 appears 1 time in count: [2, 2, 2, 1, 4, ...]
     - 3 appears 2 times in count: [2, 2, 2, 1, 4, 3, 3, ...]
     - 9 appears 1 time in count: [2, 2, 2, 1, 4, 3, 3, 9, ...]
     - 6 appears 1 time in count: [2, 2, 2, 1, 4, 3, 3, 9, 6, ...]
     - Remaining elements will be handled in the next step.
     ```

4. **Fill `ans` array with remaining elements**
   - Iterate through the `count` array and place remaining elements in `ans`.
     ```
     After processing remaining elements:
     ans = [2, 2, 2, 1, 4, 3, 3, 9, 6, 7, 19]
     Explanation:
     - 7 appears 1 time in count and is placed in ans: [2, 2, 2, 1, 4, 3, 3, 9, 6, 7, ...]
     - 19 appears 1 time in count and is placed in ans: [2, 2, 2, 1, 4, 3, 3, 9, 6, 7, 19, ...]
     ```

### Final Result
- `ans = [2, 2, 2, 1, 4, 3, 3, 9, 6, 7, 19]`

### Conclusion
The function `relativeSortArray` sorts `arr1` such that the elements present in `arr2` appear first in the order they are in `arr2` and the remaining elements are sorted in ascending order.
