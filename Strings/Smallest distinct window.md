Given a string '**s**'. The task is to find the **smallest** window length that contains all the characters of the given string at least one time.  
For eg. A = **aabcbcdbca**, then the result would be 4 as of the smallest window will be **dbca**.

**Example 1:**

Input : "AABBBCBBAC"
Output : 3
Explanation : Sub-string -> "BAC"

```java
class Solution {
    public int findSubString( String str) {
         if(str.length() == 0) return 0;
        Set<Character> set = new HashSet<>();
        for(Character ch : str.toCharArray()) set.add(ch);
        
        Map<Character,Integer> map = new HashMap<>();
        int i = 0;
        int j = 0;
        int len = Integer.MAX_VALUE;
        
        while(j < str.length()){
            char chj = str.charAt(j);
            map.put(chj , map.getOrDefault(chj,0) + 1);
            
            while(map.size() == set.size()){
                len = Math.min(len , j - i + 1);
                char chi = str.charAt(i);
                map.put(chi, map.get(chi) - 1);
                
                if(map.get(chi) == 0){
                    map.remove(chi);
                }
                
                i++;
            }
            j++;
            
        }
        
        return len;
        
    }
}
```