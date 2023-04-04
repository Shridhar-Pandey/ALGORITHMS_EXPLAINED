***Segmented Sieve (Print Primes in a Range)***

The Segmented Sieve algorithm is used to identify all prime integers that are less than n. The principle behind this algorithm is to calculate primes in each segment of the range [0, n-1] one by one. To discover primes smaller than or equal to, this algorithm first employs the Simple Sieve method.(n).

Here are the procedures for a segmented sieve.

1. Create an array called "prime[]" and use Simple Sieve to discover all prime numbers up to the square root of "n".

2. Split the interval [0, n-1) into a number of segments, each of dimension d. There could be fewer than 'd' components in the final segment.

3. Sieve each of the segments individually, beginning with the shortest, using the primes discovered in step 1.

4. Mark all multiples of the primes discovered in step 1 that are contained within each section.

<hr>

***Psedocode***


``` psedocode
function segmentedSieve (n):
    limit = floor(sqrt(n))+1
    primes = simpleSieve(limit)
    low = limit
    high = 2*limit
    while low < n:
        if high >= n:
            high = n
        mark = [True]*limit
        for i in range(len(primes)):
            loLim = floor(low/primes[i]) * primes[i]
            if loLim < low:
                loLim += primes[i]
            for j in range(loLim, high, primes[i]):
                mark[j-low] = False
        for i in range(low, high):
            if mark[i - low]:
                print(i)
        low = low + limit
        high = high + limit

function simpleSieve(limit):
    primes = []
    mark = [True]*(limit+1)
    p = 2
    while p*p <= limit:
        if mark[p]:
            for i in range(p*p, limit+1, p):
                mark[i] = False
        p += 1
    for p in range(2, limit):
        if mark[p]:
            primes.append(p)
    return primes
```

<hr>

***Python code for Segmented Sieve Algorithm***


``` py
import math

def simpleSieve(limit, primes):
    mark = [True]*(limit+1)
    p = 2
    while p*p <= limit:
        if mark[p]:
            for i in range(p*p, limit+1, p):
                mark[i] = False
        p += 1
    for p in range(2, limit):
        if mark[p]:
            primes.append(p)

def primesInRange(low, high):
    limit = int(math.floor(math.sqrt(high))+1)
    primes = []
    simpleSieve(limit, primes)
    n = high - low + 1
    mark = [True]*n
    for i in range(len(primes)):
        loLim = int(math.floor(low/primes[i]) * primes[i])
        if loLim < low:
            loLim += primes[i]
        for j in range(loLim, high+1, primes[i]):
            if j != primes[i]:
                mark[j-low] = False
            else:
                mark[j-low] = True
    for i in range(low, high+1):
        if mark[i-low]:
            print(i)

low = int(input())
high = int(input())
primesInRange(low, high)
```

<hr>

***Java code for Segmented Sieve Algorithm***


``` java
import java.util.ArrayList;
import java.util.Scanner;

public class Main {
    
    public static void simpleSieve(int limit, ArrayList<Integer> primes) {
        boolean[] mark = new boolean[limit+1];
        for (int p = 2; p*p <= limit; p++) {
            if (!mark[p]) {
                for (int i = p*p; i <= limit; i += p) {
                    mark[i] = true;
                }
            }
        }
        for (int p = 2; p < limit; p++) {
            if (!mark[p]) {
                primes.add(p);
            }
        }
    }
    
    public static void primesInRange(int low, int high) {
        int limit = (int)Math.floor(Math.sqrt(high))+1;
        ArrayList<Integer> primes = new ArrayList<>();
        simpleSieve(limit, primes);
        int n = high - low + 1;
        boolean[] mark = new boolean[n];
        for (int i = 0; i < primes.size(); i++) {
            int loLim = (int)Math.floor(low/primes.get(i)) * primes.get(i);
            if (loLim < low) {
                loLim += primes.get(i);
            }
            for (int j = loLim; j <= high; j += primes.get(i)) {
                if (j != primes.get(i)) {
                    mark[j-low] = true;
                }
            }
        }
        for (int i = low; i <= high; i++) {
            if (!mark[i-low]) {
                System.out.println(i);
            }
        }
    }
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int low = scanner.nextInt();
        int high = scanner.nextInt();
        primesInRange(low, high);
    }
}

```








