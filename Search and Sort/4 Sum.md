Given an array **A** of integers and another number **K**. Find all the **unique** quadruple from the given array that sums up to **K**.

Also note that all the quadruples which you return should be internally sorted, ie for any quadruple [q1, q2, q3, q4] the following should follow: q1 <= q2 <= q3 <= q4.

**Example 2:**

**Input:**
N = 7, K = 23
A[] = {10,2,3,4,5,7,8}
**Output:** 2 3 8 10 
        2 4 7 10 
        3 5 7 8 **Explanation:** Sum of 2, 3, 8, 10 = 23,
sum of 2, 4, 7, 10 = 23 and sum of 3,
5, 7, 8 = 23.

```java
// arr[] : int input array of integers
// k : the quadruple sum required

class Solution {
    public ArrayList<ArrayList<Integer>> fourSum(int[] arr, int k) {
         ArrayList<ArrayList<Integer>> ans = new ArrayList<>();
        int n = arr.length;
        if (n < 4) return ans;

        Arrays.sort(arr);
        for (int i = 0; i < n - 3; i++) {
            if (i > 0 && arr[i] == arr[i - 1]) continue; // skip duplicates
            for (int j = i + 1; j < n - 2; j++) {
                if (j > i + 1 && arr[j] == arr[j - 1]) continue; // skip duplicates

                int left = j + 1, right = n - 1;
                while (left < right) {
                    int sum = arr[i] + arr[j] + arr[left] + arr[right];
                    if (sum == k) {
                        ArrayList<Integer> temp = new ArrayList<>();
                        temp.add(arr[i]);
                        temp.add(arr[j]);
                        temp.add(arr[left]);
                        temp.add(arr[right]);
                        ans.add(temp);

                        while (left < right && arr[left] == arr[left + 1]) left++;
                        while (left < right && arr[right] == arr[right - 1])

                        right--;
                        left++;
                        right--;
                    } 
                    else if (sum < k) left++;
                    else right--;
                }
            }
        }
      return ans;
    }
}
```