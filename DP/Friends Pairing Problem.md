**Question:**
Given N friends, each one can remain single or can be paired up with some other friend. Each friend can be paired only once. Find out the total number of ways in which friends can remain single or can be paired up.  
Note: Since answer can be very large, return your answer mod 10^9+7.

  
**Example 1:**

**Input:**N = 3
**Output:** 4
**Explanation**:
{1}, {2}, {3} : All single
{1}, {2,3} : 2 and 3 paired but 1 is single.
{1,2}, {3} : 1 and 2 are paired but 3 is single.
{1,3}, {2} : 1 and 3 are paired but 2 is single.
Note that {1,2} and {2,1} are considered same.

**Example 2:** 

**Input**: N = 2
**Output:** 2
**Explanation**:
{1} , {2} : All single.
{1,2} : 1 and 2 are paired.

**Code:**
public long countFriendsPairings(int n) 
    { 
       //code here
        long MOD = 1000000007;
        long dp[]=new long[n+1];
        
        if(n==1)return 1;
        if(n==2)return 2;
        
        dp[0]=1;
        dp[1]=1;
        dp[2]=2;
        
        // f(n)=f(n-1)+(n-1)*f(n-2)
        //   f(n-1) -> in case 1 friend remains unpaired and the rest n-1 friends pair
        // (n-1)*f(n-2)  -> after 1 friend pairs up with somebody, n-2 
        //people remain, they can have n-1 permutations and n-2 people can pair up in f(n-2) ways
         
        for(int i=3;i<=n;i++)
        {
            dp[i] = (dp[i - 1] + ((i - 1) * dp[i - 2]) % MOD) % MOD;
        }
        return dp[n];
    }
    
**Why does this code work?**
**1. Base Cases:**

- `dp[0] = 1`: There's only one way to pair 0 friends (no friends to pair).
- `dp[1] = 1`: There's only one way to pair 1 friend (the friend stays single).
- `dp[2] = 2`: There are two ways to pair 2 friends (either both stay single or they pair up).

**2. Dynamic Programming Loop (Bottom-Up Approach):**

- The loop starts from `i = 3` because the base cases handle `n = 0`, `1`, and `2`.
- For each `i` from `3` to `n`, `dp[i]` is calculated using the recursive relation: `dp[i] = dp[i - 1] + (i - 1) * dp[i - 2]`.
    - `dp[i - 1]` represents the number of ways to pair the first `i - 1` friends. If the `i`-th friend stays single, this pairing doesn't affect the previous `i - 1` friends' pairings.
    - `(i - 1) * dp[i - 2]` represents the number of ways to pair the `i`-th friend with one of the `(i - 1)` friends. The `i - 1` choices indicate the friends the `i`-th friend can pair with, and `dp[i - 2]` represents the number of ways to pair the remaining friends.
    - The total number of ways to pair `i` friends is the sum of these two cases.

**3. Modular Arithmetic:**

- To prevent integer overflow, the code uses modular arithmetic with `MOD = 1000000007`.
- The intermediate results and the final result (`dp[i]`) are taken modulo `MOD` to ensure the values stay within a manageable range.