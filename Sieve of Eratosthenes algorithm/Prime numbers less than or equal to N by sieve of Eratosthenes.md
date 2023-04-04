***Prime numbers less than or equal to N by sieve of Eratosthenes***

Prime numbers are whole numbers larger than 1 whose only factors are themselves, as we are all familiar with. Therefore, we must comprehend the Sieve of Eratosthenes and its algorithm in order to solve this issue.



**What is the Sieve of Eratosthenes?**

The Sieve of Eratosthenes is an ancient algorithm for finding all prime numbers up to any given limit1. It works by iteratively marking as composite (i.e., not prime) the multiples of each prime, starting with the first prime number

Here’s how it works:

1. Make a list of the following sequential integers: 2, 3, 4,..., n.

2. As a starting point, set p to 2, the smallest prime integer.

3. Count the number p's multiples from p*p to n in increments of p and note each one in the list. These multiples will be 2p, 3p, 4p, etc.; the number p itself shouldn't be marked.

4.  Locate the smallest non-marked number in the list that is larger than p. Stop if there wasn't such a number. If not, set p to this new number (which is the following prime), then proceed to step 3 as normal.
By noting that all prime numbers larger than three have the shape 6k ± 11, the algorithm can be further improved.



 **Steps involved in the Sieve of Eratosthenes algorithm**
 
 1. Create integers between 2 and n. (2 is the smallest prime).

2. Start at the smallest prime integer, num, which is equal to two.

3. Eliminate or mark all num multiples that are less than or equivalent to n (as 0 or -1).

4. Track down the following larger number than num that is not denoted by a 0 or a -1.

5.Repeat steps 3 and 4 until you've gone through all the digits.

<hr>

**Psedocode**

``` psedocode

Input : Integer n, greater than 1
Output : All prime numbers in the range 1 - n

for i = 2 to n
    prime[i] = true

for i = 2 to sqrt(n)
    if (prime[i] == true)
        for j = i*i to n step i
            prime[j] = false

for i = 2 to n
    if (prime[i] == true)
        print i
    
 ```


<hr>

****Python code to impliment of Sieve of Eratosthenes algorithm****
``` py
def sieve(n):
    primes = [True] * (n+1)
    primes[0] = primes[1] = False
    for i in range(2, int(n**0.5)+1):
        if primes[i]:
            for j in range(i*i, n+1, i):
                primes[j] = False
    return [i for i in range(2, n+1) if primes[i]]

n = int(input("Enter a number: "))
print("Prime numbers smaller than or equal to", n, "are:")
print(sieve(n))
```

<hr>

****Java code to impliment of Sieve of Eratosthenes algorithm****

``` java
import java.util.ArrayList;

public class SieveOfEratosthenes {
    public static ArrayList<Integer> sieve(int n) {
        boolean[] primes = new boolean[n+1];
        ArrayList<Integer> result = new ArrayList<Integer>();
        for (int i = 2; i <= n; i++) {
            primes[i] = true;
        }
        for (int p = 2; p*p <= n; p++) {
            if (primes[p]) {
                for (int i = p*p; i <= n; i += p) {
                    primes[i] = false;
                }
            }
        }
        for (int i = 2; i <= n; i++) {
            if (primes[i]) {
                result.add(i);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        int n = Integer.parseInt(args[0]);
        System.out.println("Prime numbers smaller than or equal to " + n + " are:");
        System.out.println(sieve(n));
    }
}
```
