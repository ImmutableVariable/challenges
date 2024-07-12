# Grouping Lists Based On Their Most Common Shared Element

Given a 2d array of lists, group the lists based on their most common element. If two lists have the same most common element, they should be grouped together. For example, if [1, 2, 3] and [3, 4] have the same most common element, they should be grouped together based on that element (3). The output should be a dictionary (or hashmap) where the keys represent the most common element and the values are the lists that contain that element. Each list will only be in one grouping.

## Test Case

```
// input:
[
    ["red", "green"],
    ["red", "blue"],
    ["red"],
    ["green", "blue"],
    ["blue", "yellow"],
    ["yellow"],
    ["yellow"],
    ["yellow", "red"],
    ["red"],
    ["green", "red"],
    ["red", "green"],
];

// output: 
{
    "yellow": [["blue", "yellow"], ["yellow"], ["yellow"]], 
    "green": [["green", "blue"]], 
    "red": [["red", "green"], ["red", "blue"], ["red"], ["yellow", "red"], ["red"], ["green", "red"], ["red", "green"]], 
    "blue": [] 
    // no lists have blue as the most common element,
    // because the lists that contain blue contain other elements that are more common
    // however if you just had a list with ["blue"] in it, it would be in this list as 
    // blue: [["blue"]] as that would be the most common element globally that is also in that list
}
```
