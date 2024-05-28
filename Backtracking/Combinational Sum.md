
#string_based 
Given an array of integers and a sum B, find all unique combinations in the array where the sum is equal to B. The same number may be chosen from the array any number of times to make B.

**Note:**  
        **1.** All numbers will be positive integers.  
        **2.** Elements in a combination (a1, a2, …, ak) must be in non-descending order. (ie, a1 ≤ a2 ≤ … ≤ ak).  
        **3.** The combinations themselves must be sorted in ascending order.

  
**Example 1:**

**Input:**
N = 4
arr[] = {7,2,6,5}
B = 16
**Output:**
(2 2 2 2 2 2 2 2)
(2 2 2 2 2 6)
(2 2 2 5 5)
(2 2 5 7)
(2 2 6 6)
(2 7 7)
(5 5 6)
### Code 
```java 
static void
    findNumbers(ArrayList<ArrayList<Integer> > ans,
                ArrayList<Integer> arr, int sum, int index,
                ArrayList<Integer> temp)
    {
 
        if (sum == 0) {
 
            // Adding deep copy of list to ans
 
            ans.add(new ArrayList<>(temp));
            return;
        }
 
        for (int i = index; i < arr.size(); i++) {
 
            // checking that sum does not become negative
 
            if ((sum - arr.get(i)) >= 0) {
 
                // adding element which can contribute to
                // sum
 
                temp.add(arr.get(i));
 
                findNumbers(ans, arr, sum - arr.get(i), i,
                            temp);
 
                // removing element from list (backtracking)
                temp.remove(arr.get(i));
            }
        }
    }
```