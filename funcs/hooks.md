# Hooks

Arguably the most important feature of QSS is hooks. You can make custom code run either before or after any function in scope. Here is an example.

```text
func manipulate_entity(e: Entity) {
    // do stuff here
}

after func manipulate_entity(e: Entity) {
    // this will be called every time manipulate_entity is called
}
```

As you can see, you can insert the word `after` before the function signature to say that this code will run after the original function is called. You can do the same with the keyword `before` to make your code run before the function is called.

## Hook Powers

Hooks can manipulate the parameters of the function. Any changes made `before` the function is executed may affect the function itself. For example:

```text
func do_stuff(value: Int) {
    value.print();
}

before do_stuff(value: Int) {
    value = value + 1;
}
```

If we call `do_stuff(2)`, we will see the number `3` output to the screen. This is because the `value` parameter was edited by the hook.

`after` hooks can also edit the parameters, but this is a much more niche use case, because the function has already executed by this point.

Additionally, `after` hooks have access to the `result` variable if the function returned a value. You can manipulate `result` just like any variable.

```text
func return_one() -> Int {
    return 1;
}

after return_one() -> Int {
    return result + 1;
    // "result = result + 1" also works
}
```

Calling `return_one()` will now return `2`.

