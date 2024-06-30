# Answers

You can probably get shorter

## Javascript

```javascript
h=n=>{for(s=new Set;n!=1&&!s.has(n);s.add(n),n=n.toString().split('').reduce((a,c)=>a+c**2,0));return n==1}
```

Commented code: 
```javascript
h = n => {
    for (s = new Set; // set to store numbers
         n != 1 && !s.has(n);  // while n is not 1 and n is not in set, if n is in set, it is an infinite loop and not a happy number
         s.add(n),  // add n to set
         n = n.toString().split('').reduce((a, c) => a + c ** 2, 0)); // sum of squares of digits
    return n == 1 // return true if n is 1
}
```