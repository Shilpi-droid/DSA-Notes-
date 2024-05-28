Given an input stream **A** of **n** characters consisting only of lower case alphabets. While reading characters from the stream, you have to tell which character has appeared only once in the stream upto that point. If there are many characters that have appeared only once, you have to tell which one of them was the first one to appear. If there is no such character then append '#' to the answer.

**NOTE:  
**1. You need to find the answer for every i (0 <= i < n)  
2. In order to find the solution for every i you need to consider the string from starting position till ith position. 

**Example 1:**

**Input:** A = "aabc"
**Output:** "a#bb"
**Explanation:** For every ith character we will  
consider the string from index 0 till index i first non
repeating character is as follow-
"a" - first non-repeating character is 'a'
"aa" - no non-repeating character so '#'
"aab" - first non-repeating character is 'b'
"aabc" - there are two non repeating characters 'b' and 'c', first non-repeating character is 'b' because 'b' comes before  
'c' in the stream.

```java
//{ Driver Code Starts
import java.util.*;
import java.lang.*;
import java.io.*;
class GFG
{
    public static void main(String[] args) throws IOException
    {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter out=new PrintWriter(System.out);
        int T = Integer.parseInt(br.readLine().trim());
        while(T-->0)
        {
            String A = br.readLine().trim();
            Solution ob = new Solution();
            String ans = ob.FirstNonRepeating(A);
            out.println(ans);
        }
        out.close();
    }
}

// } Driver Code Ends


class Solution
{
    public String FirstNonRepeating(String A)
    {
        // code here
        StringBuilder s = new StringBuilder();
      HashMap<Character,Integer> map=new HashMap<>();
      Deque<Character> q=new ArrayDeque<>();
      for(int i=0;i<A.length();i++)
      {
          if(map.containsKey(A.charAt(i)))
          {
              map.put(A.charAt(i),map.get(A.charAt(i))+1);
          }
          else
          {
              map.put(A.charAt(i),1);
          }
          if(map.get(A.charAt(i))==1)
          {
              q.offer(A.charAt(i));
          }
          while(!q.isEmpty()&&map.get(q.peekFirst())>1)
          {
              q.removeFirst();
          }
          if(q.isEmpty())
            s.append('#');
          else
          s.append(q.peekFirst());
      }
      return s.toString();
    }
}
```