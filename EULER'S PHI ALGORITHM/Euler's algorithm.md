
The arithmetic function Euler's totient function, also referred to as Euler's phi function, counts the positive integers less than or equivalent to n that are comparatively prime to n. It is indicated by φ(n).

Here’s an example of how to calculate φ(8) using this algorithm:

The prime factors of 8 are 2 and 3

φ(8) = 8 * (1 - 1/2) * (1 - 1/3) = 4



***Steps of Euler's phi Algorithm***


-Start by calculating the totient value of the integer n.

-Set the outcome variable's initial value to n.

-Perform the following for each prime p-th component of n: The result value should now be updated to result = result * (1 - 1/p).

-Return the result's ultimate value.


***Psedocode***


1. Begin by calculating the totient value of the integer n.
2. Set the outcome variable's initial value to n.
3. Complete the following for each prime component p of n:
    A. Divide n by p until it stops dividing n if p divides n.
    b. Change the value of the result variable to result = result * (1 - 1/p).
4. Each prime factor of n that is greater than sqrt(n) must be counted individually.
5. Provide the result's ultimate value.


<hr>

***Python Implementation:***

```python

def phi(n):
    result = n
    p = 2
    while p * p <= n+1:
        if n % p == 0:
            while n % p == 0:
                n = n // p
            result = result * (1 - (1 / int(p)))
        p = p + 1
    if n > 1:
        result -= result // n
    return int(result)

x = int(input("Enter a number: "))
count = 0
for n in range(1, x+1):
    print("φ(", n ,",", x,") = ", phi(n))
    if phi(n) == 1:
        count += 1

print("Number of φ's present in", x, "is", count)


```
