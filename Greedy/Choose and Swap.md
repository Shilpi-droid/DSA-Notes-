You are given a string **s** of lower case english alphabets. You can choose any two characters in the string and replace all the occurences of the first character with the second character and replace all the occurences of the second character with the first character. Your aim is to find the lexicographically smallest string that can be obtained by doing this operation at most once.

**Example 1:**

**Input**:
A = "ccad"
**Output:** "aacd"
**Explanation**:
In ccad, we choose a and c and after 
doing the replacement operation once we get, 
aacd and this is the lexicographically
smallest string possible.

```java    
    String chooseandswap(String A){
        // Code Here
        char a[]=A.toCharArray();
       HashMap<Character,Integer> h=new HashMap<>();
       
        int n=a.length;  
        for(int i=0;i<n;i++){
           if(!h.containsKey(a[i]))h.put(a[i],i);
            
        }
      
        char x='a';char b='a';
        for(int i=0;i<n;i++){
            char m='a';
            boolean flag=false;
            while(m<a[i]){
                if(h.containsKey(m)&&h.get(m)>i){
                    x=a[i];
                    b=m;
                    flag=true;
                    break;
                }
                m++;
            }
            if(flag)break;
            
        }
        if(x==b)return A;
        StringBuilder ans=new StringBuilder("");
        for(char i:a){
            if(i==x){
                ans.append(b);
            }else if(i==b){
                ans.append(x);
            }else{
                ans.append(i);
            }
        }
        
        return ans.toString();
    }
    
}
```