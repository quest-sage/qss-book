# Comments

## Regular Comments

You can add comments to your code to explain what you're doing in more detail. To create a comment on a line of code, write two slashes `//` then type whatever comment you like. The compiler will ignore everything after the two slashes until a new line starts.

```text
let a = 1;  // The variable `a` is used for ...
let b = 2;  // `b` stores the value of ...
```

You can make larger comments by writing `/*` and `*/` between any text you want the compiler to ignore.

```text
let a = 1;
/*
Anything between these symbols gets ignored.
I can make this block as large or small as I like.
*/

let b = 2; /* You can also do this, but it's easier to just use a double slash. */
```

## Documentation Comments

QSS supports a special style of comments called "documentation comments" that you can place before blocks such as data structures, appends, functions, hooks, traits and trait implementations. Surround the documentation with `**` markers to tell the compiler that this is a documentation comment.

```text
**
The function `add_one` takes in an integer and increments its value by 1.
**
func add_one(value: Int) -> Int {
    return value + 1;
}
```

{% hint style="info" %}
Try to document every function and struct you make, even if you don't think anyone but yourself will use it. After all, in QSS you can hook into any function and append to any struct, so it's especially important to keep clean documentation!
{% endhint %}

When you compile your project, all documentation comments will be put into a reference document that shows all the functionality of your resource bundle.

{% hint style="danger" %}
If you try to use a documentation comment where QSS does not expect it \(i.e. not immediately before a struct, append, func, hook, trait or impl block\), the compiler will produce an error.
{% endhint %}

