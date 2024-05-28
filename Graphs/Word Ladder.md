A **transformation sequence** from word `beginWord` to word `endWord` using a dictionary `wordList` is a sequence of words `beginWord -> s1 -> s2 -> ... -> sk` such that:

- Every adjacent pair of words differs by a single letter.
- Every `si` for `1 <= i <= k` is in `wordList`. Note that `beginWord` does not need to be in `wordList`.
- `sk == endWord`

Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return _the **number of words** in the **shortest transformation sequence** from_ `beginWord` _to_ `endWord`_, or_ `0` _if no such sequence exists._

**Example 1:**

**Input:** beginWord = "hit", endWord = "cog", wordList = ["hot","dot","dog","lot","log","cog"]
**Output:** 5
**Explanation:** One shortest transformation sequence is "hit" -> "hot" -> "dot" -> "dog" -> cog", which is 5 words long.

```java
class Pair{
    String str;
    int count;
    Pair(String str,int count){
        this.str = str;
        this.count = count;
    }
}

class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {

        Queue<Pair> q = new LinkedList<>();
        Set<String> set = new HashSet<>();

        q.offer(new Pair(beginWord,1));

        for(String s : wordList)
            set.add(s);

        set.remove(beginWord);

        while(!q.isEmpty()){

            String currStr = q.peek().str;
            int currCount = q.peek().count;
            q.poll();
            int len = currStr.length();

            if(currStr.equals(endWord))
                return currCount;

            for( int i=0 ; i<len ; i++){
                for(char ch='a' ; ch<='z' ;ch++){
                    String temp = currStr.substring(0,i) + ch + currStr.substring(i+1);
                    if(set.contains(temp)){
                        set.remove(temp);
                        q.offer(new Pair(temp , currCount+1));
                    }
                } 
            }
        }

        return 0;

    }
}
```