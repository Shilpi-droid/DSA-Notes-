In operating systems that use paging for memory management, page replacement algorithm is needed to decide which page needs to be replaced when the new page comes in. Whenever a new page is referred and is not present in memory, the page fault occurs and Operating System replaces one of the existing pages with a newly needed page.

Given a sequence of pages in an array **pages[]** of length **N** and memory capacity **C**, find the number of page faults using Least Recently Used (LRU) Algorithm. 

_**Note:-** Before solving this example revising the OS LRU cache mechanism is recommended._

**Example 1:**

**Input:** N = 9, C = 4
pages = {5, 0, 1, 3, 2, 4, 1, 0, 5}
**Output:** 8
**Explaination:** memory allocated with 4 pages 5, 0, 1, 
3: page fault = 4
page number 2 is required, replaces LRU 5: 
page fault = 4+1 = 5
page number 4 is required, replaces LRU 0: 
page fault = 5 + 1 = 6
page number 1 is required which is already present: 
page fault = 6 + 0 = 6
page number 0 is required which replaces LRU 3: 
page fault = 6 + 1 = 7
page number 5 is required which replaces LRU 2: 
page fault = 7 + 1  = 8.

```java
class Solution{
    static int pageFaults(int N, int C, int pages[]){
        int faults = 0;
        LinkedHashSet<Integer> memory = new LinkedHashSet<>();
        
        for (int i = 0; i < pages.length; i++){
            int page = pages[i];
            
            // if the memory size becomes more than the capacity
            // then we need to remove the first element
            if (memory.size() > C) {
                // get the first element
                Iterator<Integer> it = memory.iterator();
                if (it.hasNext()) {
                    it.next();
                    it.remove();
                }
            }
            
            // if the memory doesn't contain the page
            // then a pagefault occurs
            boolean inMemory = memory.contains(page);
            
            
            // if the page is in memory then we will remove it 
            // and add it again so that it goes in the end
            if (!inMemory) faults++;
            else memory.remove(page);
            memory.add(page);
        }
        return faults;
    }
}
```