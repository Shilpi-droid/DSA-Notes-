Given two strings '**str1**' and '**str2**', check if these two strings are **isomorphic** to each other.  

If the characters in str1 can be changed to get str2, then two strings, str1 and str2, are isomorphic. A character must be completely swapped out for another character while maintaining the order of the characters. A character may map to itself, but no two characters may map to the same character.

**Example 1:**

**Input:**
str1 = aab
str2 = xxy
**Output:** 1
**Explanation:** There are two different characters in aab and xxy, i.e a and b with frequency 2 and 1 respectively.

```java
 public static boolean areIsomorphic(String str1,String str2)
    {
        if(str1.length()!=str2.length()) return false;
        HashMap<Character,Character> hmap = new HashMap<>();
        char val;
        for(int i=0;i<str1.length();i++){
            if(!hmap.containsKey(str1.charAt(i))){
                if(hmap.containsValue(str2.charAt(i))) return false;
                hmap.put(str1.charAt(i),str2.charAt(i));
            }else{
                val=hmap.get(str1.charAt(i));
                if(val!=str2.charAt(i)) return false;
            }
        }
        return true;
        
    }
```