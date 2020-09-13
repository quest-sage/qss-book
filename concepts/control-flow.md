# Control Flow

Control flow allows you to control which code is run and which code is skipped based on certain conditions.

## If-Else

This is the most common kind of control flow statement. If a `Bool` condition is true, the body of the `if` statement will be executed. Otherwise, it will be skipped.

```text
if condition {
    // do stuff
}
```

You can also specify an `else` block to be run if the condition is false.

```text
if condition {
    // condition was true
} else {
    // condition was false
}
```

In fact, you can chain `if` and `else` statements to create complicated conditions.

```text
if a {
    // a was true
} else if b {
    // a was false; b was true
} else if c {
    // a and b were false; c was true
} else {
    // a, b and c were false
}
```

## While Loops

You can run a piece of code over and over until a condition is false by using a `while` loop.

```text
// Prints the numbers from 1 to 10
let i = 0;
while i < 10 {
    i = i + 1;
    i.print();
}
```

## For Loops

You can iterate over each element in a `List` by using a `for` loop.

```text
// Prints the numbers from 1 to 10
// 1 to 11 is a list from 1 (inclusive) to 11 (exclusive)
for i in 1 to 11 {
    i.print();
}
```



