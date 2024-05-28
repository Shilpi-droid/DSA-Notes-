Given weights and values of **n** items, we need to put these items in a knapsack of capacity **w** to get the **maximum** total value in the knapsack.  
**Note:** Unlike 0/1 knapsack, you are **allowed** to break the item here. 

**Example 1:**

**Input:**
n = 3   
w = 50
value[] = {60,100,120}
weight[] = {10,20,30}
**Output:**
240.000000
**Explanation:**Take the item with value 60 and weight 10, value 100 and weight 20 and split the third item with value 120 and weight 30, to fit it into weight 20. so it becomes (120/30)*20=80, so the total value becomes 60+100+80.0=240.0Thus, total maximum value of item we can have is 240.00 from the given capacity of sack.

```java
/*
class Item {
    int value, weight;
    Item(int x, int y){
        this.value = x;
        this.weight = y;
    }
}
*/

class Solution {
    // Function to get the maximum total value in the knapsack.
    double fractionalKnapsack(int W, Item arr[], int n) {
         Arrays.sort(arr,(a,b) -> (a.value*b.weight) - (b.value*a.weight));
        
        double res = 0;
        
        for(int i = n-1;i>=0;i--)
        {
            if(arr[i].weight <= W)
            {
                res = res + arr[i].value;
                W = W - arr[i].weight;
            }
            else
            {
                res = res + arr[i].value *((double)W/(double)arr[i].weight);
                break;
            }
        }
        return res;
    }
}
```