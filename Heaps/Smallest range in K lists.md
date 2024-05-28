Given **K** sorted lists of integers, **KSortedArray[]** of size **N** each. The task is to find the smallest range that includes at least one element from each of the **K** lists. If more than one such range's are found, return the first such range found.

**Example 1:**

**Input:**
N = 5, K = 3
KSortedArray[][] = {{1 3 5 7 9},
                    {0 2 4 6 8},
                    {2 3 5 7 11}}
**Output:** 1 2
**Explanation:** K = 3
A:[1 3 5 7 9]
B:[0 2 4 6 8]
C:[2 3 5 7 11]
Smallest range is formed by number 1
present in first list and 2 is present
in both 2nd and 3rd list.

```java
class Node {
    int data;
    int row;
    int col;

    Node(int data, int i, int j) {
        this.data = data;
        row = i;
        col = j;
    }
}
class Solution
{
	static int[] findSmallestRange(int[][] KSortedArray,int n,int k)
	{
	    PriorityQueue<Node> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a.data));
        int maxi = Integer.MIN_VALUE;
        int mini = Integer.MAX_VALUE;
        for (int i = 0; i < k; i++) {
            Node temp = new Node(KSortedArray[i][0], i, 0);
            mini = Math.min(mini, temp.data);
            maxi = Math.max(maxi, temp.data);
            pq.add(temp);
        }
        int start = mini, end = maxi;
        while (!pq.isEmpty()) {
            Node temp = pq.poll();
            mini = temp.data;
            int row = temp.row;
            int col = temp.col;
            if (maxi - mini < end - start) {
                start = mini;
                end = maxi;
            }
            if (col + 1 < n) {
                Node next = new Node(KSortedArray[row][col + 1], row, col + 1);
                maxi = Math.max(maxi, KSortedArray[row][col + 1]);
                pq.add(next);
            } else {
                break;
            }
        }
        return new int[]{start, end};
	}
}

```