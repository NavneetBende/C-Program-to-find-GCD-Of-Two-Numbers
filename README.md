# C-Program-to-find-GCD-Of-Two-Numbers

GCD of Two numbers in C
Here, in this section, we will discuss the GCD of two numbers in C. The Highest Common Multiple or the Greatest Common Divisor is the greatest number that exactly divides both numbers.

Example:-

The G.C.D of 14 and 40 is 8.

The G.C.D of 18 and 12 is 9
GCD
Various Methods to calculate the GCD
Using Prime Factorization,
Euclid’s Algorithm,
Lehmer’s GCD algorithm
Method 1
For a user input n1 & n2.

Use a for loop linearly traversing such that (i <= num1 || i <= num2)
Find max i value such that both n1 and n2 are divisible by i
(num1 % i == 0 && num2 % i == 0)
C Code (Method 1)
Run
#include<stdio.h>

int main()
{
    int n1 = 18, n2 = 45, gcd = 1;
    
    for(int i = 1; i <= n1 || i <= n2; i++) {
        if(n1 % i == 0 && n2 % i == 0)
            gcd = i;
    }
    
    printf("The GCD of %d and %d is: %d", n1, n2, gcd);
    
    return 0;
}
// Time complexity : O(N)
// Space complexity : O(1)
Output
The GCD of 18 and 45 is: 9
Related Pages
Lowest Common Multiple (LCM)

Highest Common Factor(HCF)
 
Binary to Decimal to conversion

Octal to Decimal conversion

Hexadecimal to Decimal conversion

Method 2 
Euclidean Algorithm (also known as repeated Subtraction) is used for this method 

Euclidean Algorithm: GCD of two numbers remains constant even if we subtract the smaller number from the higher number.
Below is an example of a manual calculation that you can understand before moving ahead with the code.

Example -
Let m = 104, n = 24

m > n
m = m – n = 104 – 24 = 80
now m = 80, n = 24

m = m – n = 80 – 24 = 56
now m = 56, n = 24

m = m – n = 56 – 24 = 32
now m = 32, n = 24

m = m – n = 32 – 24 = 8
now m = 8, n = 24

Since, m < n
Now, we will need to change subtraction order.

n = n – m = 24 – 8 = 16
now m = 8, n = 16

n = n – m = 16 – 8 = 8
now m = 8, n = 8

m = n. So, stop. GCD = 8
C Code (Method 2)
Run
#include<stdio.h>

// Using Euclidean Algorithm (Repeated Subtraction)
int main()
{
    int n1 = 104, n2 = 24, gcd = 1;
    
    while (n1 != n2)
    {
        if (n1 > n2)
            n1 -= n2;
        else
            n2 -= n1;
    }
    
    printf("The GCD: %d", n1, n2, gcd);
    
    return 0;
}
Output
The GCD: 8
Method 3
Euclidean Algorithm (also known as repeated Subtraction) is again used for this method 

This method has two changes –

Uses recursive approach
Also, handles if one of the numbers is 0
Handling one of the number being 0
In previous codes, we ignored if one of the numbers happened to be 0.

GCD of two numbers will be the larger number, if one of the numbers is zero
Example GCF of 0 and 12 will be 12
C Code (Method 3)
Run
#include<stdio.h>

// Using Recursive Euclidean Algorithm (Repeated Subtraction)
int calcGCD(int n1, int n2)
{
    // Takes care of the case n1 is 0
    // We have given explanation above
    if (n1 == 0)
       return n2;
    
    // Takes care of the case n2 is 0
    // We have given explanation above
    if (n2 == 0)
       return n1;
  
    // base case
    if (n1 == n2)
        return n1;
  
    // n1 is greater
    if (n1 > n2)
        return calcGCD(n1 - n2, n2);

    // n2 is greater
    return calcGCD(n1, n2 - n1);
}

int main()
{
    int n1 = 45, n2 = 18;

    int gcd = calcGCD(n1, n2);
    
    printf("The GCD of %d and %d is: %d", n1, n2, gcd);
    
    return 0;
}
Output
The GCD of 45 and 18 is: 9
Method 4
Euclidean Algorithm (also known as repeated Subtraction) is again used for this method 

This method has two changes –

Reduced number of subtraction
Modulo operation helps us achieve these reduce subtraction
C Code (Method 4)
Run
#include<stdio.h>

// Improved the time complexity in comparision to repeated subtraction
// Done by efficient usage of modulo operator in euclidean algorithm
int calcGCD(int a, int b)
{
    return b == 0 ? a : calcGCD(b, a % b);   
}

int main()
{
    int n1 = 45, n2 = 18;

    int gcd = calcGCD(n1, n2);
    
    printf("The GCD of %d and %d is: %d", n1, n2, gcd);
    
    return 0;
}
Output
The GCD of 45 and 18 is: 9
