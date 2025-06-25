
#Math  #Recursion 
time limit per test

1 second

memory limit per test

256 megabytes

The gcdSumgcdSum of a positive integer is the gcdgcd of that integer with its sum of digits. Formally, gcdSum(x)=gcd(x, sum of digits of x)gcdSum(x)=gcd(x, sum of digits of x) for a positive integer xx. gcd(a,b)gcd(a,b) denotes the greatest common divisor of aa and bb — the largest integer dd such that both integers aa and bb are divisible by dd.

For example: gcdSum(762)=gcd(762,7+6+2)=gcd(762,15)=3gcdSum(762)=gcd(762,7+6+2)=gcd(762,15)=3.

Given an integer nn, find the smallest integer x≥nx≥n such that gcdSum(x)>1gcdSum(x)>1.

Input

The first line of input contains one integer tt (1≤t≤104)(1≤t≤104) — the number of test cases.

Then tt lines follow, each containing a single integer nn (1≤n≤1018)(1≤n≤1018).

All test cases in one test are different.

Output

Output tt lines, where the ii-th line is a single integer containing the answer to the ii-th test case.

Example

Input

Copy

3
11
31
75

Output

Copy

12
33
75

Note

Let us explain the three test cases in the sample.

Test case 1: n=11n=11:

gcdSum(11)=gcd(11,1+1)=gcd(11, 2)=1gcdSum(11)=gcd(11,1+1)=gcd(11, 2)=1.

gcdSum(12)=gcd(12,1+2)=gcd(12, 3)=3gcdSum(12)=gcd(12,1+2)=gcd(12, 3)=3.

So the smallest number ≥11≥11 whose gcdSumgcdSum >1>1 is 1212.

Test case 2: n=31n=31:

gcdSum(31)=gcd(31,3+1)=gcd(31, 4)=1gcdSum(31)=gcd(31,3+1)=gcd(31, 4)=1.

gcdSum(32)=gcd(32,3+2)=gcd(32, 5)=1gcdSum(32)=gcd(32,3+2)=gcd(32, 5)=1.

gcdSum(33)=gcd(33,3+3)=gcd(33, 6)=3gcdSum(33)=gcd(33,3+3)=gcd(33, 6)=3.

So the smallest number ≥31≥31 whose gcdSumgcdSum >1>1 is 3333.

Test case 3:  n=75 n=75:

gcdSum(75)=gcd(75,7+5)=gcd(75, 12)=3gcdSum(75)=gcd(75,7+5)=gcd(75, 12)=3.

The gcdSumgcdSum of 7575 is already >1>1. Hence, it is the answer.