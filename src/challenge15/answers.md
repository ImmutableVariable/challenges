# Answer

## Python

```py
from itertools import permutations
from math import factorial

def is_prime(x):
    return factorial(x - 1) % x == x - 1

def circular_prime(n: int):
    digits = [int(i) for i in str(n)]
    for x in permutations(digits):
        if not is_prime(int("".join([str(i) for i in x]))):
            return False
        
        return True
    
print(circular_prime(197))
```