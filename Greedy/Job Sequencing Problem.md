Given a set of **N** jobs where each **jobi** has a deadline and profit associated with it.

Each job takes **_1_** unit of time to complete and only one job can be scheduled at a time. We earn the profit associated with job if and only if the job is completed by its deadline.

Find the number of jobs done and the **maximum profit**.

**Note:** Jobs will be given in the form (Jobid, Deadline, Profit) associated with that Job. Deadline of the job is the time before which job needs to be completed to earn the profit.

  
**Example 1:**

**Input:**
N = 4
Jobs = {(1,4,20),(2,1,10),(3,1,40),(4,1,30)}
**Output:**
2 60
**Explanation:**
Job1 and Job3 can be done with
maximum profit of 60 (20+40).


```java
class Solution
{
    //Function to find the maximum profit and the number of jobs done.
    int[] JobScheduling(Job arr[], int n)
    {
        Arrays.sort(arr,(a,b)->b.profit-a.profit);
        
        int maxi=0;
        for(int i=0;i<n;i++){
            
            maxi= Math.max(arr[i].deadline,maxi);
        }
        int []res=new int[maxi+1];
        Arrays.fill(res,-1);
        
        
        int profit=0;
        int ids=0;
        
        for(int i=0;i<n;i++){
            
            for(int j=arr[i].deadline;j>0;j--){
                if(res[j]==-1){
                    res[j]=i;
                    ids++;
                    profit+=arr[i].profit;
                    break;
                }
            }
        }
        
        return new int[]{ids,profit};
    }
}

/*
class Job {
    int id, profit, deadline;
    Job(int x, int y, int z){
        this.id = x;
        this.deadline = y;
        this.profit = z; 
    }
}
*/
```