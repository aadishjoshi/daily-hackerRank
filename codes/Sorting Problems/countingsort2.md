# Counting sort 2


https://www.hackerrank.com/challenges/countingsort2/problem


```

import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the countingSort function below.
    static int[] countingSort(int[] arr) {

        int n = arr.length;

        int [] a = new int[100];

        for(int i=0;i<n;i++){
            a[arr[i]] += 1;
        }

        int j = 0;
        while(j<99){
            a[j+1] = a[j+1]+a[j];
            j +=1;
        }
        //a[j] = a[j]+a[j-1];
        
        // for(int j=1; j<101;j++){
        //     a[j] = a[j] + a[j-1];
        // }

        int [] anew = new int[n+1];

        for(int k=0;k<n; k++){
            anew[a[arr[k]]] = arr[k];
            a[arr[k]] = a[arr[k]] - 1;
        }

        return anew;
    }

    private static final Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) throws IOException {
        BufferedWriter bufferedWriter = new BufferedWriter(new FileWriter(System.getenv("OUTPUT_PATH")));

        int n = scanner.nextInt();
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        int[] arr = new int[n];

        String[] arrItems = scanner.nextLine().split(" ");
        scanner.skip("(\r\n|[\n\r\u2028\u2029\u0085])?");

        for (int i = 0; i < n; i++) {
            int arrItem = Integer.parseInt(arrItems[i]);
            arr[i] = arrItem;
        }

        int[] result = countingSort(arr);

        for (int i = 1; i < result.length; i++) {
            bufferedWriter.write(String.valueOf(result[i]));

            if (i != result.length - 1) {
                bufferedWriter.write(" ");
            }
        }

        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}



```