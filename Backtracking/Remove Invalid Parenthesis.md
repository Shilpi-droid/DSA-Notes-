 #string_based
Given a string `s` that contains parentheses and letters, remove the minimum number of invalid parentheses to make the input string valid.

Return _a list of **unique strings** that are valid with the minimum number of removals_. You may return the answer in **any order**.

**Example 1:**

**Input:** s = "()())()"
**Output:** ["(())()","()()()"]
### Code

```java
class Solution {
    public List<String> removeInvalidParentheses(String s) {
      HashSet<String>hs=new HashSet<>();
      int mra=getMin(s);
      solution(s,0,mra,0,hs);
      List<String> arrayList = new ArrayList<>();
      arrayList.addAll(hs);
        return arrayList;
    }

     public static void solution(String str, int index, int mra, int removals, HashSet<String> hs) {
        if (index == str.length()) {
            if (mra == 0 && removals == 0) {
                hs.add(str);
            }
            return;
        }

        char ch = str.charAt(index);

        // Remove current character
        solution(str.substring(0, index) + str.substring(index + 1), index, mra, removals - 1, hs);

        // Keep current character
        solution(str, index + 1, mra - (ch == '(' ? 1 : 0) + (ch == ')' ? 1 : 0), removals, hs);
    }

       public static int getMin(String str) {
        Stack<Character> st = new Stack<>();
        int removals = 0;

        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);

            if (ch == '(') {
                st.push(ch);
            } else if (ch == ')') {
                if (!st.isEmpty() && st.peek() == '(') {
                    st.pop();
                } else {
                    removals++;
                }
            }
        }
        return st.size() + removals;
    }

}
```