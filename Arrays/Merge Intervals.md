### Question
Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return _an array of the non-overlapping intervals that cover all the intervals in the input_.

**Example 1:**

**Input:** intervals = [[1,3],[2,6],[8,10],[15,18]]
**Output:** [[1,6],[8,10],[15,18]]
**Explanation:** Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

### Code
```java
 public int[][] merge(int[][] arr)

    {
        int n=arr.length;
         Arrays.sort(arr, new Comparator<int[]>() {
            public int compare(int[] a, int[] b) {
                return a[0] - b[0];
            }

        });
        List<List<Integer>> ans=new ArrayList<>();
        for(int i=0;i<n;i++)
        {
           if(ans.isEmpty()|| arr[i][0]>ans.get(ans.size()-1).get(1))
            {
               ans.add(Arrays.asList(arr[i][0], arr[i][1]));
            }
            else
            {
                ans.get(ans.size()-1).set(1,Math.max(arr[i][1],ans.get(ans.size()-1).get(1)));
            }
        }
        int [][]merged_int=new int[ans.size()][2];
        for(int i=0;i<ans.size();i++)
        {
            merged_int[i][0]=ans.get(i).get(0);
            merged_int[i][1]=ans.get(i).get(1);
        }
        return merged_int;
    }
```
