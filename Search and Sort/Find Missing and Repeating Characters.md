
```java
//{ Driver Code Starts
// Initial Template for Java

import java.io.*;
import java.util.*;

class GFG {
    // Driver code
    public static void main(String[] args) throws Exception {
        BufferedReader br =
            new BufferedReader(new InputStreamReader(System.in));
        int t = Integer.parseInt(br.readLine().trim());
        while (t-- > 0) {
            int n = Integer.parseInt(br.readLine().trim());
            String[] str = br.readLine().split(" ");

            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = Integer.parseInt(str[i]);
            }

            int[] ans = new Solve().findTwoElement(a, n);
            System.out.println(ans[0] + " " + ans[1]);
        }
    }
}
// } Driver Code Ends


// User function Template for Java

class Solve {
    int[] findTwoElement(int arr[], int n) {
        // code here
         Arrays.sort(arr);

        int[] result = new int[2];
        
        int sum = arr[0], totalSum = 1;
        
        for(int i=n-1; i>0; i--){
            totalSum += i + 1;
            
            if(arr[i] == arr[i-1]){
                
                result[0] = arr[i];
                
            }else{
                sum += arr[i];
            }
            
        }
        

        result[1] = totalSum - sum;
        
        return result;
    }
    
}
```