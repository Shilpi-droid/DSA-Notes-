You are given N pairs of numbers. In every pair, the first number is always smaller than the second number. A pair (c, d) can follow another pair (a, b) if b < c. Chain of pairs can be formed in this fashion. You have to find the longest chain which can be formed from the given set of pairs.   
 

**Example 1:**

**Input:**
N = 5
P[] = {5  24 , 39 60 , 15 28 , 27 40 , 50 90}
**Output:** 3
**Explanation**: The given pairs are { {5, 24}, {39, 60},
{15, 28}, {27, 40}, {50, 90} },the longest chain that
can be formed is of length 3, and the chain is
{{5, 24}, {27, 40}, {50, 90}}


```java
int maxChainLength(Pair arr[], int n)
    {
       Arrays.sort(arr,(a,b)->a.y-b.y); // sort it by 2nd value;
       //2 pointers
       int i = 0;
       int j = 1;
       int count = 1; // count variable for longestt chain
       
       while( j  < n){
           if(arr[i].y < arr[j].x){
               count++;
                i = j;
                j++;
           }else{
               j++;
           }
       }
       return count;
    }
```