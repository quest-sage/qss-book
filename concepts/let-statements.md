# Let Statements

You can create new variables by writing a `let` statement. For example:

```text
let a = 1;
```

This code fragment creates a new variable called `a` and assigns it the value `1`. You don't need to tell QSS explicitly what data type `a` is; it can infer it from context.

If you want to declare a variable without assigning it a value, you need to tell QSS what type it is.

```text
let a: Int;
// some time later...
a = 1;
```

{% hint style="danger" %}
You can't use a variable before assigning a value to it. The compiler will emit an error if you haven't assigned the variable before using it.
{% endhint %}



