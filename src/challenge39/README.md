# Cash To Coins

Create a function that accepts a float value representing a amount of money (Ex: $2.75) and returns a the number of each coins/dollars required to make that amount of money. It should always return the smallest number of coins/dollars possible.

```
cash_to_coins(2.75) -> {
    "dollars": 2,
    "quarters": 3,
    "dimes": 0,
    "nickels": 0,
    "pennies": 0
}

cash_to_coins(0.99) -> {
    "dollars": 0,
    "quarters": 3,
    "dimes": 2,
    "nickels": 0,
    "pennies": 4
}

cash_to_coins(100.75) -> {
    "dollars": 100,
    "quarters": 3,
    "dimes": 0,
    "nickels": 0,
    "pennies": 0
}
```