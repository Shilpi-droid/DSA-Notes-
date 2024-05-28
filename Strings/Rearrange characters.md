Given a string S with repeated characters. The task is to rearrange characters in a string such that no two adjacent characters are the same.  
**Note:** The string has only lowercase English alphabets and it can have multiple solutions. Return any one of them.

**Example 1:**

**Input :** str = "geeksforgeeks"
**Output:** 1
**Explanation:** All the repeated characters of the
given string can be rearranged so that no 
adjacent characters in the string is equal.
Any correct rearrangement will show a output
of 1.

```java
class Solution
{
	public static String rearrangeCharacters(String s) {
	
		StringBuilder str=new StringBuilder(s);
        HashMap<Character,Integer> m=new HashMap<>();
        for(int i=0;i<str.length();i++){
            m.put(str.charAt(i),m.getOrDefault(str.charAt(i),0)+1);
        }
        char ch='a';
        int x=Integer.MIN_VALUE;
        for(Map.Entry<Character,Integer> e:m.entrySet()){
            if(e.getValue()>x){
                x=e.getValue();
                ch=e.getKey();
            }
        }
        int i=0;
        while(x>0&&i<str.length()){
            str.setCharAt(i,ch);
            x--;
            i+=2;
        }
        if(x>0)
        return "-1";
        m.remove(ch);
            for(Map.Entry<Character,Integer> e:m.entrySet()){
            int v=e.getValue();
            while(v>0){
            if(i>=str.length())
            i=1;
            str.setCharAt(i,e.getKey());
            v--;
            i+=2;
            }
        }
        return str.toString();
	}
}
```