# Hooking Variables

You can hook more than just function executions. You can also write code to be run whenever a variable's value is retrieved or set, using `get` and `set` hooks.

```text
struct A {
    x: Int
    set_count: Int
}

before set A.x(this: A, value: Int) {
    this.set_count = this.set_count + 1;
}
```

The `set_count` variable tracks how many times `A.x` has been set.

TODO: the validation for set/get hooks is broken in the current version of QSS; they accept any function signature. Also, the validation for `new Struct {}` expressions is broken; you can define any amount of fields in the block.

