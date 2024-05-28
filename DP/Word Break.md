Given a string **s** and a dictionary of **n** words **dictionary**, find out if "**s"** can be segmented into a space-separated sequence of dictionary words.  
Return 1 if it is possible to break the **s** into a sequence of dictionary words, else return 0. 

**Note:** From the dictionary **dictionary** each word can be taken any number of times and in any order.

**Example 1:**

**Input:**
n = 6  
s = "ilike"  
dictionary = { "i", "like", "sam", "sung", "samsung", "mobile"}  
**Output:**
1
**Explanation:**
The string can be segmented as "i like".


```java
public static int wordBreak(int n, String s, ArrayList<String> dictionary )
    {
        //code here
        HashMap<String, Integer> m = new HashMap<>();
        for (String word : dictionary) 
            m.put(word, m.getOrDefault(word, 0) + 1);

        int np = s.length();
        int[] dp = new int[np];

        String u = s.substring(0, 1);
        if (m.containsKey(u))
            dp[0] = 1;

        for (int i = 1; i < np; i++) {
            for (int j = 0; j < i; j++) {
                if (dp[j] == 1 && m.containsKey(s.substring(j + 1, i + 1)))
                    dp[i] = 1;
            }
            if (m.containsKey(s.substring(0, i + 1)))
                dp[i] = 1;
        }

        return dp[np - 1];
    }
```
