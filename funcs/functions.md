# Functions

This is the syntax for defining functions in QSS.

```text
func function_name() {
    // do stuff here
}
```

You can pass parameters to the function by declaring them between the parentheses. You need to tell QSS what type the variables are by using the `name: Type` syntax you saw with [let statements](../concepts/let-statements.md).

```text
func do_stuff_with_numbers(left: Int, right: Int) {
    // do stuff here
}
```

If your function returns a value, you need to write the return type at the end of the function type like this:

```text
func add_two_numbers(left: Int, right: Int) -> Int {
    return left + right;
}
```

{% hint style="danger" %}
If you define a return value, but do not return anything, the compiler will emit an error.
{% endhint %}



