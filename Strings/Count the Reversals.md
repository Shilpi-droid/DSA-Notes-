Given a string **S** consisting of only opening and closing curly brackets **'{'** and **'}',** find out the minimum number of reversals required to convert the string into a balanced expression.  
A reversal means changing **'{'** to **'}'** or vice-versa.

**Example 1:**

**Input:**
S = "}{{}}{{{"
**Output:** 3
**Explanation**: One way to balance is:
"**{**{{}}{**}}**". There is no balanced sequence
that can be formed in lesser reversals.

```java
class Sol
{
    int countRev (String s)
    {
        int cnt=0;
        Stack<Character> st=new Stack<Character>();
         for(int i=0; i<s.length(); i++){
            char m=s.charAt(i);
            if(!st.isEmpty() && (m=='}')){
                if(st.peek()=='{'){
                    st.pop();
                }
                else{
                    st.push(m);
                }
            }
            else{
                st.push(m);
            }
        }
        while(st.size()>=2){
            char m1=st.pop();
            char m2=st.pop();
            
            if(m1==m2){
                cnt=cnt+1;
            }
            else{
                cnt=cnt+2;
            }
        }
         if(!st.isEmpty()){
            return -1;
        }
        
        return cnt;
    }
}
```