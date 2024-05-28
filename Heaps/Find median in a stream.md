Given an input stream of **N** integers. The task is to insert these numbers into a new stream and find the median of the stream formed by each insertion of **X** to the new stream.

**Example 1:**

**Input:**
N = 4
X[] = 5,15,1,3
**Output:**
5
10
5
4
**Explanation:**Flow in stream : 5, 15, 1, 3 
5 goes to stream --> median 5 (5) 
15 goes to stream --> median 10 (5,15) 
1 goes to stream --> median 5 (5,15,1) 
3 goes to stream --> median 4 (5,15,1 3)

```java
class Solution
{ static PriorityQueue<Integer> left=new PriorityQueue<>(Collections.reverseOrder());
    static PriorityQueue<Integer> right=new PriorityQueue<>();
    
    public static void insertHeap(int x){
        if(left.size()==0){
            left.add(x);
        }
        else if(left.size()>right.size()){
            right.add(x);
            balanceHeaps();
        }
        else{
            left.add(x);
            balanceHeaps();
        }
    }
    public static void balanceHeaps(){
        if(left.peek()>right.peek()){
            int temp1=left.poll();
            int temp2=right.poll();
            left.add(temp2);
            right.add(temp1);
        }
    }
    
    //Function to return Median.
    public static double getMedian(){
        if(left.size()>right.size()){
            return (double)left.peek();
        }
        else{
            int x=left.peek();
            int y=right.peek();
            double res=(x+y)/2;
            return res;
        }
    }
    
}
```