Given elements as nodes of the two linked lists. The task is to multiply these two linked lists, say L1 and L2. 

**Note:** The output could be large take modulo 109+7.

**Example:**

**Input:**
2
2
3 2
1
2
3
1 0 0
2
1 0 
**Output:**
64
1000

**Explanation:
Testcase 1:** 32*2 = 64.
**Testcase 2:** 100*10 = 1000.

```java
class GfG{
     private static final int MOD = 1000000007;
  /*You are required to complete this method */
   public long multiplyTwoLists(Node l1,Node l2){
          //add code here.
           long num1 = 0;
          long num2 = 0;
          
          while(l1 != null || l2 != null){
              if(l1!=null){
                  num1=((num1*10)+l1.data)%MOD;
                  l1 = l1.next;
              }if(l2!=null){
                  num2=((num2*10)+l2.data)%MOD;
                  l2=l2.next;
              }
          }
          return (num1*num2)%MOD;
   }
}
```