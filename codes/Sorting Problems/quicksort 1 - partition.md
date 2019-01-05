# QuickSort 1 partition

https://www.hackerrank.com/challenges/quicksort1/problem

```
import java.io.*;
import java.math.*;
import java.security.*;
import java.text.*;
import java.util.*;
import java.util.concurrent.*;
import java.util.regex.*;

public class Solution {

    // Complete the quickSort function below.
    static void quickSort(int[] arr, int p, int r) {
        if(p<r){
            int q = partition(arr, p ,r);
            quickSort(arr,p,q-1);
            quickSort(arr,q+1,r);
        }
    }

    static int partition(int [] arr, int p, int r){
        int x  = arr[r];
        int i = p-1;

        int temp1, temp2;

        for(int j = p;j <r; j++){
            if(arr[j] <= x){
                i += 1;
                temp1 = arr[j];
                arr[j] = arr[i];
                arr[i] = temp1;
            }
        }
        
        temp2 = arr[r];
        arr[r] = arr[i+1];
        arr[i+1] = temp2;

        return i+1;
        

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

        quickSort(arr,0,arr.length-1);

        for (int i = 0; i < arr.length; i++) {
            bufferedWriter.write(String.valueOf(arr[i]));

            if (i != arr.length - 1) {
                bufferedWriter.write(" ");
            }
        }

        bufferedWriter.newLine();

        bufferedWriter.close();

        scanner.close();
    }
}


```