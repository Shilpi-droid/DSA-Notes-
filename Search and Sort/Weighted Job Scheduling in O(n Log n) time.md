Given N jobs where every job is represented by following three elements of it.

1. Start Time
2. Finish Time
3. Profit or Value Associated

Find the maximum profit subset of jobs such that no two jobs in the subset overlap.  
Example: 

Input: Number of Jobs n = 4
       Job Details {Start Time, Finish Time, Profit}
       Job 1:  {1, 2, 50} 
       Job 2:  {3, 5, 20}
       Job 3:  {6, 19, 100}
       Job 4:  {2, 100, 200}
Output: The maximum profit is 250.
We can get the maximum profit by scheduling jobs 1 and 4.
Note that there is longer schedules possible Jobs 1, 2 and 3 
but the profit with this schedule is 20+50+100 which is less than 250.

The above problem can be solved using following recursive solution. 

1) First sort jobs according to finish time.
2) Now apply following recursive process. 
   // Here arr[] is array of n jobs
   findMaximumProfit(arr[], n)
   {
     a) if (n == 1) return arr[0];
     b) Return the maximum of following two profits.
         (i) Maximum profit by excluding current job, i.e., 
             findMaximumProfit(arr, n-1)
         (ii) Maximum profit by including the current job            
   }

**How to find the profit including current job?**
The idea is to find the latest job before the current job (in 
sorted array) that doesn't conflict with current job 'arr[n-1]'. 
Once we find such a job, we recur for all jobs till that job and
add profit of current job to result.
In the above example, "job 1" is the latest non-conflicting
for "job 4" and "job 2" is the latest non-conflicting for "job 3".

```java
// Java program for Weighted Job Scheduling in O(nLogn)
// time
import java.util.Arrays;
import java.util.Comparator;

// Class to represent a job
class Job
{
	int start, finish, profit;

	// Constructor
	Job(int start, int finish, int profit)
	{
		this.start = start;
		this.finish = finish;
		this.profit = profit;
	}
}

// Used to sort job according to finish times
class JobComparator implements Comparator<Job>
{
	public int compare(Job a, Job b)
	{
		return a.finish < b.finish ? -1 : a.finish == b.finish ? 0 : 1;
	}
}

public class WeightedIntervalScheduling
{
	/* A Binary Search based function to find the latest job
	(before current job) that doesn't conflict with current
	job. "index" is index of the current job. This function
	returns -1 if all jobs before index conflict with it.
	The array jobs[] is sorted in increasing order of finish
	time. */
	static public int binarySearch(Job jobs[], int index)
	{
		// Initialize 'lo' and 'hi' for Binary Search
		int lo = 0, hi = index - 1;

		// Perform binary Search iteratively
		while (lo <= hi)
		{
			int mid = (lo + hi) / 2;
			if (jobs[mid].finish <= jobs[index].start)
			{
				if (jobs[mid + 1].finish <= jobs[index].start)
					lo = mid + 1;
				else
					return mid;
			}
			else
				hi = mid - 1;
		}

		return -1;
	}

	// The main function that returns the maximum possible
	// profit from given array of jobs
	static public int schedule(Job jobs[])
	{
		// Sort jobs according to finish time
		Arrays.sort(jobs, new JobComparator());

		// Create an array to store solutions of subproblems.
		// table[i] stores the profit for jobs till jobs[i]
		// (including jobs[i])
		int n = jobs.length;
		int table[] = new int[n];
		table[0] = jobs[0].profit;

		// Fill entries in M[] using recursive property
		for (int i=1; i<n; i++)
		{
			// Find profit including the current job
			int inclProf = jobs[i].profit;
			int l = binarySearch(jobs, i);
			if (l != -1)
				inclProf += table[l];

			// Store maximum of including and excluding
			table[i] = Math.max(inclProf, table[i-1]);
		}

		return table[n-1];
	}

	// Driver method to test above
	public static void main(String[] args)
	{
		Job jobs[] = {new Job(1, 2, 50), new Job(3, 5, 20),
					new Job(6, 19, 100), new Job(2, 100, 200)};

		System.out.println("Optimal profit is " + schedule(jobs));
	}
}

```