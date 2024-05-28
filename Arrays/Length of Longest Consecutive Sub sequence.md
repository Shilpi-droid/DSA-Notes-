### Question 

Given an array of positive integers. Find the length of the longest sub-sequence such that elements in the subsequence are consecutive integers, the **consecutive numbers can be in any order.**  
 

**Example 1:**

**Input:**
N = 7
a[] = {2,6,1,9,4,5,3}
**Output:**
6
**Explanation:**
The consecutive numbers here
are 1, 2, 3, 4, 5, 6. These 6 
numbers form the longest consecutive
subsquence.

### Code 
```java
static int findLongestConseqSubseq(int arr[], int n)
	{
	   
        HashSet<Integer> S = new HashSet<Integer>();
        int ans = 0;
 
        // Hash all the array elements
        for (int i = 0; i < n; ++i)
            S.add(arr[i]);
 
        // check each possible sequence from the start
        // then update optimal length
        for (int i = 0; i < n; ++i) {
            // if current element is the starting
            // element of a sequence
            if (!S.contains(arr[i] - 1)) {
                // Then check for next elements
                // in the sequence
                int j = arr[i];
                while (S.contains(j)){
                      S.remove(Integer.valueOf(j));//this will improve runtime by avoiding the repetitive counts of elements
                    j++;
                    }
 
                // update  optimal length if this
                // length is more
                if (ans < j - arr[i])
                    ans = j - arr[i];
            }
        }
        return ans;
	}
```