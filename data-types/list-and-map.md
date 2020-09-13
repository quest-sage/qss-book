# List and Map

## List

You can make a list of variables of the same type by writing `new List <Type>`. Write each variable out in a block, separated by semicolons. For example:

```text
let list = new List Int { 1; 2; 3; };  // list: List Int
```

You can retrieve values from the list by using square bracket notation.

```text
let head = list[0];
```

The data type of `head` is `Maybe Int`. If element `0` was in the list, `head` will contain the value of the list element. If the list did not contain a `0`th element, `head` will be null. This means that the square bracket operator never causes your program to crash. Here is a program that prints each element of a list.

```text
let list = new List Int { 1; 1; 2; 3; 5; 8; };
let i = 0;
while exists list[i] {
    (get list[i]).print();
    i = i + 1;
}
```

## Map

You can make a map \(like a Python dict or a Java Map\) that maps keys to values by writing `new Map <Key> To <Value>`. Write each comma-separated entry out in a block, separated by semicolons. For example:

```text
let map = new Map Int To String {
    1, "hello";
    2, "world";
};  // map: Map Int To String
```

You can use the same square bracket syntax to retrieve values from the map.

```text
let hello = map[1];
if exists hello {
    (get hello).print();
}
```

If no mapping is present for the given key, `null` is returned.

