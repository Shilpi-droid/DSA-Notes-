- Move all negative elements to the other side of the array 
```java
class Solution {
    
    public void segregateElements(int arr[], int n)
    {
        int temp[]=new int[n];
        int j=0;
        for(int i=0;i<n;i++)
        {
            if(arr[i]>0)
                temp[j++]=arr[i];
            
        }
        for(int i=0;i<n;i++)
        {
            if(arr[i]<0)
                temp[j++]=arr[i];
        }
        for(int i=0;i<n;i++)
        {
            arr[i]=temp[i];
            
        }
    }
    
}
```

- Best Time to buy and sell stock 

	```java
	public int maxProfit(int[] prices) {
        int minSoFar=Integer.MAX_VALUE;
        int maxProfit=0;
        for(int i=0;i<prices.length;i++)
        {
            minSoFar=Math.min(minSoFar,prices[i]);
            maxProfit=Math.max(maxProfit,prices[i]-minSoFar);
        }
        return maxProfit;
    }
```

- Count pairs with a given sum

```java
	int getPairsCount(int[] arr, int n, int k) {
         HashMap<Integer, Integer> m = new HashMap<>();
         int count=0;
         for(int i=0;i<n;i++)
         {
            if(m.containsKey(k-arr[i]))
                count+=m.get(k-arr[i]);
            if(m.containsKey(arr[i]))
                m.put(arr[i],m.get(arr[i])+1);
            else m.put(arr[i],1);
         }
         return count;
    }
```

- Find common elements between 3 sorted arrays
	```java
	class Solution  
{  
    ArrayList<Integer> commonElements(int arr1[], int arr2[], int arr3[], int n1, int n2, int n3)   
    {  
        // code here   
        ArrayList<Integer> list = common(arr1,arr2);  
        int[] temp= new int[list.size()];  
        for(int i=0;i< list.size();i++){  
            temp[i]= list.get(i);  
        }  
        ArrayList<Integer> list1 = common(temp,arr3);  
        return list1;  
    }  
      
    private static ArrayList<Integer> common(int[] arr1, int[] arr2) {  
        int i=0;  
        int j=0;  
        ArrayList<Integer> list = new ArrayList<>();  
        while(i< arr1.length && j< arr2.length){  
//            System.out.println(i);  
            if(arr1[i] == arr2[j]){  
                if(i<arr1.length-1 && arr1[i]==arr1[i+1]){  
                    i= i+1;  
                }  
                else{  
                list.add(arr1[i]);  
                i = i+1;  
                j = j+1;  
                }  
            }  
            else if(arr1[i] < arr2[j]){  
                i = i+1;  
            }  
            else{  
                j = j+1;  
            }  
        }  
        return list;  
    }  
}
```

-rearrange the array into alternate positive and negative arrays(similar to merge sort)
```java
void rearrange(int arr[], int n) {
        
        int pos[]=new int[n];
        int neg[]=new int[n];
        int pptr=0;
        int nptr=0;
        
        for(int i = 0; i < n; i++)
        {
            if(arr[i]>=0)
            {
                pos[pptr]=arr[i];
                pptr++;
            }
            else
            {
                neg[nptr]=arr[i];
                nptr++;
            }
        }
        int i=0;int j=0;int k=0;
        while(j<pptr && k<nptr)
        {
            arr[i]=pos[j];
            arr[i+1]=neg[k];
            i+=2;
            j++;
            k++;
        }
        while(j<pptr)
        {
            arr[i++]=pos[j++];
        }
        while(k<nptr)
        {
            arr[i++]=neg[k++];
        }
        
    }
```
 - Check if the array has a subarray of sum 0 //important
 ```java
 static boolean findsum(int arr[],int n)
    {
        //Your code here
        HashMap<Integer,Boolean> h=new HashMap<>();
       int sum=0;
       for(int i=0; i<n; i++)
       {
           sum+=arr[i];
           if(h.containsKey(sum)  || sum==0){
               return true;
           }
           else{
               h.put(sum,false);
           }
       }
       return false;
    }
```

- factorial of a large number// didn't understand 

```java
static ArrayList<Integer> factorial(int n){
        //code here
        ArrayList<Integer>result=new ArrayList<>();
        int size=0,c=0;
        result.add(0,1);
        // updating size
        size=1;
        //Declare a value to traverse the array from n to 2
        int val=2;
        while(val<=n)
        {
            //Traverse the arraylist from right to left
            for(int i=size-1;i>=0;i--)
            {
                //Update the value in the arrayList
                int temp=result.get(i)*val+c;
                result.set(i,temp%10);
                //update carry 
                c=temp/10;
                
            }
            //insert carry digit by digit at the beginning of the arraylist while(c!=0)
            {
                result.add(0,c%10);
                c=c/10;
                size++;
            }
            val++;
        }
        
        return result;
    }
```
- triplet sum 
	- [[2 pointer Algorithm]]
```java
public static boolean find3Numbers(int a[], int n, int X) { 
        
     Arrays.sort(a);
    
     int sum=0;
     for(int i =0 ; i<n; i++)
     {
        int left=i+1;
        int right=n-1;
            
         while(left<right)
         {
             sum=a[i]+a[left]+a[right];
             if(sum==X)
                return true;
                
            else if(sum<X)
                left++;
            else right--;
         }
     }
     return false;
    
    }
```