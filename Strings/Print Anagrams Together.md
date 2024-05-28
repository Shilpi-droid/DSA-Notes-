Given an array of strings, return all groups of strings that are anagrams. The groups must be created in order of their appearance in the original array. Look at the sample case for clarification.

**Note: The final output will be in lexicographic order.**

  
**Example 1:**

**Input:**
N = 5
words[] = {act,god,cat,dog,tac}
**Output:**
act cat tac 
god dog
**Explanation:**
There are 2 groups of
anagrams "god", "dog" make group 1.
"act", "cat", "tac" make group 2.

```java
class Solution {
    public List<List<String>> Anagrams(String[] string_list) {
        HashMap<String, List<String>> map = new HashMap<>();
        for (String word : string_list) {
            char[] characters = word.toCharArray();
            Arrays.sort(characters);
            String sortedWord = new String(characters);
            if (!map.containsKey(sortedWord)) {
                map.put(sortedWord, new ArrayList<>());
            }
            map.get(sortedWord).add(word);
        }
        return new ArrayList<>(map.values());
    }
}
```