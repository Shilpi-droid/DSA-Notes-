Given a fence with **n** posts and **k** colors, find out the number of ways of painting the fence so that **not more than two** consecutive posts have the same colors. Since the answer can be large return it **modulo 109 + 7.**

**Example 1:**

**Input:**
n = 3  
k = 2 
**Output:** 6
**Explanation**:   
Let the 2 colours be 'R' and 'B'.  
We have following possible combinations:  
1. RRB
2. RBR
3. RBB
4. BRR
5. BRB
6. BBR

```java
class Solution
{
    long countWays(int n,int k)
    {
        long mod = 1000000007;
        long Same = 0;
        long Diff = k;
        
        for(int i=2;i<=n;i++){
            long temp = Same;
            Same = Diff;
            Diff = ((temp + Diff)%mod * (k-1)%mod)%mod;
        }
        
        return (Same+Diff)%mod;
    }
}
```