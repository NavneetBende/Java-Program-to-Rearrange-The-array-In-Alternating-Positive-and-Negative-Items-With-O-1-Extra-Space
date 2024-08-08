Rearrange the Array in Java
Here, on this page, we will discuss the program to Rearrange the Array in Java. Rearrange in the way of alternating positive and negative items. Here, we will also discuss the efficient way of solving this problem in O(1) extra space. We are given an array of positive and negative numbers, we have to arrange them.
A number of positive and negative numbers need not be equal. If there are more positive numbers they appear at the end of the array. If there are more negative numbers, they too appear at the end of the array.

Program to Rearrange The array In Alternating Positive and Negative Items
Let’s discuss the brute force approach to solve this problem. As, here we need to maintain the order of the array and also solve this problem in O(1) extra space means without using extra space.

Method 1 – Brute force approach
Take the size of the array from the user and store it in variable say n.
Now, declare an array of n size and named it let say arr[], take n integer value from the user and store them in the created array.
Now, we will rearrange the array by using the following approach :
Iterate array from left to right i.e, 0 to n-1 index value. While iterating, find the first out of place element in the remaining unprocessed array.
An element is out of place if it is negative and at odd index, or it is positive and at even index.
Once we get an out of place element, we find the first element after it with opposite sign.
Then, We right rotate the sub-array between these two elements (including these two).
Now, the above approach takes O(N^2) time and O(1) space to solve the problem. In the second method we will discuss an efficient way to solve this problem.

Rearrange the array in C++
Code to rearrange the array in Java
Run
import java.io.*;
import java.lang.*;
import java.util.*;
public
class Main {
    static void fill1(int a[], int neg, int pos) {
        if (neg % 2 == 1) {
            for (int i = 1; i < neg; i += 2) {
                int c = a[i];
                int d = a[i + neg];
                int temp = c;
                a[i] = d;
                a[i + neg] = temp;
            }
        } else {
            for (int i = 1; i <= neg; i += 2) {
                int c = a[i];
                int d = a[i + neg - 1];
                int temp = c;
                a[i] = d;
                a[i + neg - 1] = temp;
            }
        }
    }
    static void fill2(int a[], int neg, int pos) {
        if (pos % 2 == 1) {
            for (int i = 1; i < pos; i += 2) {
                int c = a[i];
                int d = a[i + pos];
                int temp = c;
                a[i] = d;
                a[i + pos] = temp;
            }
        } else {
            for (int i = 1; i <= pos; i += 2) {
                int c = a[i];
                int d = a[i + pos - 1];
                int temp = c;
                a[i] = d;
                a[i + pos - 1] = temp;
            }
        }
    }
    // Reverse the array
    static void reverse(int a[], int n) {
        int i, k, t;
        for (i = 0; i < n / 2; i++) {
            t = a[i];
            a[i] = a[n - i - 1];
            a[n - i - 1] = t;
        }
    }
    // Print the array
    static void print(int a[], int n) {
        for (int i = 0; i < n; i++) System.out.print(a[i] + " ");
        System.out.println();
    }
    // Driver Code
    public
    static void main(String[] args) throws java.lang.Exception {
        // Given array
        int[] arr = {-1, 6, -2, 3, -4, 9};
        int n = arr.length;
        System.out.println("Given array is ");
        print(arr, n);
        int neg = 0, pos = 0;
        for (int i = 0; i < n; i++) {
            if (arr[i] < 0)
                neg++;
            else
                pos++;
        }
        // Sort the array
        Arrays.sort(arr);
        if (neg <= pos) {
            fill1(arr, neg, pos);
        } else {
            // reverse the array in this condition
            reverse(arr, n);
            fill2(arr, neg, pos);
        }
        System.out.println("Rearranged array is ");
        print(arr, n);
    }
}
Given array is 
-1 6 -2 3 -4 9 
Rearranged array is 
-4 6 -1 3 -2 9 
