Given **K** sorted arrays arranged in the form of a matrix of size K*K. The task is to merge them into one sorted array.  
**Example 1:**

**Input:**
K = 3
arr[][] = {{1,2,3},{4,5,6},{7,8,9}}
**Output:** 1 2 3 4 5 6 7 8 9
**Explanation:**Above test case has 3 sorted
arrays of size 3, 3, 3
arr[][] = [[1, 2, 3],[4, 5, 6], 
[7, 8, 9]]
The merged list will be 
[1, 2, 3, 4, 5, 6, 7, 8, 9].

```java
{
    //Function to merge k sorted arrays.
    public static ArrayList<Integer> mergeKArrays(int[][] arr,int K) 
    {
        ArrayList<Integer> ans = new ArrayList<>();
        
        PriorityQueue<Item> pq = new PriorityQueue<>(new ItemComparator());
        
        // Insert first element of all array
        for (int i = 0; i < K; i++) {
            Item item = new Item(arr[i][0], i, 0);
            pq.add(item);
        }
        
        while (!pq.isEmpty()) {
            Item root = pq.remove();
            
            ans.add(root.data);
            
            int row = root.row;
            int col = root.col;
            
            if (col + 1 < arr[row].length) {
                Item item = new Item(arr[row][col + 1], row, col + 1);
                pq.add(item);
            }
        }
        
        return ans;
        
    }
    
    private static class ItemComparator implements Comparator<Item> {
        
        public int compare(Item i1, Item i2) {
            if (i1.data < i2.data) return -1;
            if (i1.data > i2.data) return 1;
            
            return 0;
        }
    }
    
    private static class Item {
        
        int data = 0;
        int row = 0;
        int col = 0;
        
        Item(int data, int row, int col) {
            this.data = data;
            this.row = row;
            this.col = col;
        }
    }
```