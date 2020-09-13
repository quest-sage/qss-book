# Purity

Functions in QSS have a purity associated with them. By default, functions in QSS are "impure", meaning that they are allowed to basically do anything, including modifying the tabletop state. In certain scenarios, we need to guarantee that calling a function will not change the tabletop state; such functions are called "pure". To define a pure function, write the keyword `pure` before the `func` keyword.

```text
pure func add_one(value: Int) -> Int {
    return value + 1;
}
```

{% hint style="info" %}
Don't make functions pure unless you need to. It severely restricts what you are allowed to do in the body of the function.
{% endhint %}

## Purity Keywords

There are three kinds of purity in QSS.

### Impure

Impure is the default purity. You can modify anything freely inside an impure function. You may call impure functions and pure functions when inside an impure function. Because they edit the tabletop, impure functions are synchronised across all clients connected to a server - all clients are _guaranteed_ to execute the same functions in the same order.

### Pure

Pure functions \(`pure func`\) have no effects on the tabletop. They cannot edit or mutate their parameters. You may only call pure functions when inside a pure function. Because of the lack of effects, clients may freely execute pure functions without even alerting the server that they've done it. One use for this is pathfinding - only the user who wants to move an entity has to run the pathfinding code. If it's marked as a pure function, it's guaranteed to avoid desynchronisation, no matter what code is used or what hooks are made.

### UI

UI functions \(`ui func`\) have no effects on the tabletop, but may create, destroy or manipulate user interface elements. You can call pure and UI functions inside the body of a UI function.

## Hooks and Purity

If you want to hook into a function that has a purity tag, you must also write the purity tag on your hook. For example:

```text
pure func a() {}
before pure func a() {
    // hook code goes here
}
```

You are restricted to the same purity level in hooks as you are in the original function.

{% hint style="info" %}
Changing the purity of a function is a breaking change. Hooks that depend on this function will need to be rewritten if you change a function's purity. Consider the use cases of each function you write before deciding its purity.
{% endhint %}

