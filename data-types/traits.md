# Traits

Traits are a way of adding dynamic behaviour to data types that all have something in common. Traits let us write code in generic ways without needing to know exactly what data type something is. You've already seen traits in action, but maybe you didn't realise it!

## Animals Example

Here's an example using an animal-related example.

```text
trait Animal {
    pure func amount_of_legs(this: This) -> Int
}
```

This code says that if a variable is an `Animal`, then we can run the function `amount_of_legs` to find out how many legs it has. We'll explain the syntax more later, but for now just remember that the `amount_of_legs` function will work on any `Animal`. Let's create some animals to show how this code works.

```text
struct Dog {}
impl Animal for Dog {
    pure func amount_of_legs(this: This) -> Int {
        // All dogs have 4 legs.
        return 4;
    }
}
```

On Line 2, we implement the `Animal` trait for the `Dog` data type. If you're familiar with Java, this is like implementing an interface. If you come from a C++ background, it's like extending a class of pure virtual functions.

When we implement a trait for a type, we need to tell QSS what code we want to run for each function. On Line 3 we implement the function `amount_of_legs` for `Dog`. This block will be run whenever we call the function `amount_of_legs` on a `Dog`. If we call `amount_of_legs` on a different animal, a different block specific to that animal will be called.

```text
let dog = new Dog {};
dog.amount_of_legs().print();  // prints 4
```

Let's create some more animals with their own implementations.

```text
struct Spider {}
impl Animal for Spider {
    pure func amount_of_legs(this: This) -> Int {
        // All spiders have 8 legs.
        return 8;
    }
}

struct Centipede {
    ** Centipedes can have anywhere from 15 to 170-ish pairs of legs. **
    leg_pairs: Int
}
impl Animal for Centipede {
    pure func amount_of_legs(this: This) -> Int {
        return this.leg_pairs * 2;
    }
}
```

We can call the function `amount_of_legs` on any of these implementations of `Animal`.

```text
let spider = new Spider {};
spider.amount_of_legs().print();  // prints 8

let centipede = new Centipede { leg_pairs = 38; };
centipede.amount_of_legs().print();  // prints 76
```

## Debug Trait

Here is some code from the `std::debug` package.

```text
trait Debug {
    pure func debug(this: This) -> String
}
```

This code introduces a trait called `Debug`. Data types can "implement" the `Debug` trait, allowing us to use the functions in `Debug` on that type. For example:

```text
let one_string = 1.debug();
let half_string = (1/2).debug();
```

Because the `Debug` trait is implemented for `Int`, we can call the `debug` function on the value `1`. The `Debug` trait is also implemented for `Ratio`, so we can call the `debug` function on the value `1/2`.

## The This Type

In trait blocks, you will see the `This` type used quite frequently. It is best illustrated with an example:

```text
impl Animal for Dog {
    // Here, This = Dog
}

impl Animal for Spider {
    // Here, This = Spider
}
```

`This` refers to the concrete type that we're implementing a trait for. Because we don't know what the type is when we're defining a trait, we can just use `This` as a substitute.

Every function defined in a trait is written in receiver style, and the first parameter has type `This`. You can also use the `This` type in other places, most commonly in the return type. Here's an example from the `Clone` trait.

```text
**
The Clone trait allows you to make a deep copy of a variable.
**
trait Clone {
    func clone(this: This) -> This
}
```

If you call `clone` on, for example, an `Int`, the return type will also be `Int`. If you call `clone` on a generic type like `Any Clone`, the return type will also be `Any Clone`.

In an `impl` block, we already know what the type of `This` is, so we can freely interchange the keyword `This` for the actual type.

{% tabs %}
{% tab title="This keyword" %}
```text
impl Clone for Int {
    func clone(this: This) -> This {
        return this;
    }
}
```
{% endtab %}

{% tab title="Concrete type" %}
```
impl Clone for Int {
    func clone(this: Int) -> Int {
        return this;
    }
}
```
{% endtab %}
{% endtabs %}

Here's a contrived example that shows other ways to use `This`.

```text
**
The IntoList trait allows you to convert a variable into a list
containing just that variable.
**
trait IntoList {
    func into_list(this: This) -> List This
}

impl IntoList for Int {
    func into_list(this: This) -> List This {
        return new List Int { this; };
    }
}
```

## The Any Type

You can create functions that take in any implementation of a trait. Continuing with the animal example, let's make a function that takes in two animals and works out which animal has more legs.

```text
func get_most_legs(left: Any Animal, right: Any Animal) -> Any Animal {
    if left.amount_of_legs() > right.amount_of_legs() {
        return left;
    } else {
        return right;
    }
}
```

Because this code works no matter what kind of `Animal` we have, the type of each parameter is `Any Animal`.

