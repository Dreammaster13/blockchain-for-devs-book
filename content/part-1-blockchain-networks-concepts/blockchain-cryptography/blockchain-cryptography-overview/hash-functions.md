# Hashing and Hash Functions

In computer programming **hash functions **map text \(or other data\) to integer numbers. Usually different inputs maps to different outputs, but sometimes a **collision** may happen \(different input with the same output\). The process of calculating the value of certain hash function is called "**hashing**".

![](/assets/hash-function.jpg)

In the above example the text `John Smith` is hashed to the hash value `02` and `Lisa Smith` is hashed to `01`. The input texts `John Smith` and `Sandra Dee` both are hashed to `02` and this is called "**collision**".

In programming hash functions are used in the implementation of the data structure **hash-table** \(associative array\) which maps values of certain input type to values of another type, e.g. map product name \(text\) to product price \(decimal number\).

