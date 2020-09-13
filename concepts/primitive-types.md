# Primitive Types

Many of the data types used in QSS will be familiar to programmers. However, some of the type system in QSS is specifically catered to the unique requirements of Quest Sage. All data types in QSS are written in `UpperCamelCase`.

This is a list of all the primitive data types in QSS.

| Type | Description |
| :--- | :--- |
| `Int` | Integers \(whole numbers\). The value of an `Int` can be anywhere from the minimum value$$-2^{64}$$  to the maximum value $$2^{63}-1$$. |
| `Bool` | Either the value `true` or `false`. |
| `String` | Raw text that the user can input, for example a name. |
| `Text` | Text that can be translated to a user's language. Used for things like UI elements because these can be translated. |
| `Entity` | Any entity on the tabletop. |
| `Ratio` | Rational numbers, such as fractions or decimals. This is used to calculate exact divisions of numbers, which can be rounded using various rounding rules. |
| `Col` | A colour. This has red, green, blue and alpha \(transparency\) channels. |
| `Pos` | A two-dimensional position on the tabletop. If a hexagonal grid is used, the x axis is tilted anticlockwise by 30° to align with the grid. |
| `Stat` |  An `Int` that keeps track of how it has changed over time. This is deprecated and will be removed from the language soon! |
| `Texture` | An image that can be assigned to entities on the tabletop to control how they look. |

### Large Ints

You can use underscores in `Int` literals to increase legibility. For example, the number $$10^9$$ could be written `1_000_000_000`.

### Text and String

When possible, use `Text` instead of `String`. This allows for much greater flexibility in how the text can be displayed on the user's screen, and it opens up your script to be translated into other languages. However, when users input text, they only input it in their own language, so we are forced to use a raw `String` here. The best ways to use these data types will be covered in later articles all about `Text`.

### Using Pos

It is not recommended to directly set the `x` and `y` coordinates of a `Pos`, because this will have different outcomes on square and hexagonal grids. There are functions designed to help with simple tasks that consider the grid type - or at least, there will be once I make them!

### Floating Point Computation

There is no floating-point data type, only exact fractional data types. This means that we have to do away with such mathematical concepts as logarithms, fractional powers, square roots, and even constants such as $$\pi$$. As of now, this has not become a problem, but if we end up hitting roadblocks due to the absence of imprecise types, we may add one.

### Boolean Logic

You can manipulate `Bool` values using the familiar logic operators `not`, `and`, `or`. For example:

```text
let a = true;
let b = false;
let c = a and b;
let d = not c;
let e = (a or d) and (not c);
```

