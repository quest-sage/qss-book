# Maybe and Null

Inspired by languages such as Rust and Haskell, QSS has no generic 'null' type to represent some kind of failed operation - instead, functions should use the `Maybe` type, which explicitly represents the possibility that the operation could fail. This has benefits especially when using hooks, because you can guarantee that you will never run into an unexpected null value, even when someone else has hooked into your functions.

A common place you will see the `Maybe` type is with entities' components. Imagine that we want to check if an entity \(called `e` in this code\) has a component called `TestComponent`.

```text
let maybe_my_component = e.TestComponent;
```

The type of the `maybe_my_component` variable is `Maybe TextComponent`. This shows that the entity might have the component, or it might not. We can check whether the component actually exists or not using the following code:

```text
if exists maybe_my_component {
    let my_component = get maybe_my_component;
    // do stuff with my_component
}
```

You can see the `exists` and `get` operators in action here. `exists` checks whether a `Maybe` value has data in it, and `get` retrieves this data.

{% hint style="danger" %}
Your code will crash if you call`get` on a `Maybe` value that does not exist.
{% endhint %}

### Creating Maybe Values

Recall that a `Maybe` value can either contain some data, or it could contain nothing. To create a `Maybe` value that contains a variable, write `just` before the variable.

```text
let a: Maybe Int;
a = just 2;
```

You can create a `Maybe` value that contains no data by writing `Null` before the variable type. You need to specify the variable type here because otherwise QSS can't determine what kind of `Maybe` you want to make.

```text
let a: Maybe Int;
a = null Int;
```

