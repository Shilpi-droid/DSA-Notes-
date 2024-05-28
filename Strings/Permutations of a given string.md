Given a string **S**. The task is to print all **unique** permutations of the given string that may contain dulplicates in lexicographically sorted order. 

**Example 1:**

**Input:** ABC
**Output:**
ABC ACB BAC BCA CAB CBA
**Explanation:**
Given string ABC has permutations in 6 
forms as ABC, ACB, BAC, BCA, CAB and CBA .

```java


class Solution {
    public List<String> find_permutation(String S) {
        
        char[]arr=S.toCharArray();
        List<List<Character>> ans = new ArrayList<List<Character>>();
        boolean[]freq=new boolean[S.length()];
        List<Character>ds=new ArrayList<>();
         for(int i=0;i<arr.length;i++)
        {
            freq[i]=false;
        }
        
        recurPermute(ans,freq,ds,arr);
        
        HashSet<String>set=new HashSet<>();
        for(int i=0;i<ans.size();i++)
        {
            set.add(charToString(ans.get(i)));
        }
        List<String>final_ans=new ArrayList<String>(set);
        Collections.sort(final_ans);
        // for(int i=0;i<ans.size();i++)
        // {
        //     final_ans.add(set.);
        // }
        return final_ans;
        
    }
    
    
    private void recurPermute(List<List<Character>>ans,boolean[]freq,List<Character>ds,char[]arr)
    {
       if (ds.size() == arr.length) {
        ans.add(new ArrayList<>(ds));
        return;
    }
    for (int i = 0; i < arr.length; i++) {
        if (!freq[i]) {
            freq[i] = true;
            ds.add(arr[i]);
            recurPermute(ans, freq, ds, arr);
            ds.remove(ds.size() - 1);
            freq[i] = false;
        }
    }
        
    }
    
    private String charToString(List<Character>arr)
    {
        String s="";
        
        for(int i=0;i<arr.size();i++)
        {
            s+=arr.get(i);
        }
        return s;
    }
}
```