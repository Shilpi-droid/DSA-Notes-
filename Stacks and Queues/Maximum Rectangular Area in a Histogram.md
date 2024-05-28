
Find the largest rectangular area possible in a given histogram where the largest rectangle can be made of a number of contiguous bars. For simplicity, assume that all bars have the same width and the width is **1 unit**, there will be **N** bars height of each bar will be given by the array **arr**.

**Example 1:**

**Input:**
N = 7
arr[] = {6,2,5,4,5,1,6}
**Output:** 12
**Explanation:** In this example the largest area would be 12 of height 4 and width 3. We can achieve this   
area by choosing 3rd, 4th and 5th bars.
![](http://d1hyf4ir1gqw6c.cloudfront.net/wp-content/uploads/histogram1.png)

```java

class Solution {
    private static long[] nextSmaller(long[] arr, long n) {
        Stack<Long> st = new Stack<>();
        st.add(-1L);
        long[] ans = new long[(int)n];

        for (int i = (int)n - 1; i >= 0; i--) {
            long curr = arr[i];

            while (st.peek() != -1 && arr[st.peek().intValue()] >= curr) {
                st.pop();
            }
            ans[i] = st.peek();
            st.add((long)i);
        }
        return ans;
    }
    
    private static long[] prevSmaller(long[] arr, long n) {
        Stack<Long> st = new Stack<>();
        st.add(-1L);
        long[] ans = new long[(int)n];

        for (int i = 0; i < n; i++) {
            long curr = arr[i];

            while (st.peek() != -1 && arr[st.peek().intValue()] >= curr) {
                st.pop();
            }
            ans[i] = st.peek();
            st.add((long)i);
        }
        return ans;
    }

    public static long getMaxArea(long[] hist, long n) {
        long[] next = nextSmaller(hist, n);
        long[] prev = prevSmaller(hist, n);
        long area = Long.MIN_VALUE;

        for (int i = 0; i < n; i++) {
            long l = hist[i];
            if (next[i] == -1) {
                next[i] = n;
            }
            long b = next[i] - prev[i] - 1;

            long newArea = l * b;
            area = Math.max(area, newArea);
        }
        return area;
    }
}

```