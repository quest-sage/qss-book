# Hello, World!

## Making a Resource Bundle

To get started writing code in QSS, you will need to make a Quest Sage resource bundle to put your resources in. This should be made into a simple button press in future versions of Quest Sage.

Your `hello_world.qss` file should look like this:

```text
package <your_package_name>

import std::entity
import std::debug

after func spawn_entity() -> Entity {
    "Hello, World!".print();
}
```

## The Hello, World program

If you're familiar with Java, the first few lines may look similar to Java code. You start by defining a `package`, which is basically the folder the code is stored in.

Then follows a list of imports, which tell the compiler what other bits of code you want to use in your program. In our case, we import `std::entity` and `std::debug`.

{% hint style="info" %}
Whenever you want to use code from another package in your program, you need to import the package.
{% endhint %}

Lines 6-8 demonstrate a core feature of QSS, hooks. We will go more in detail later, but for now all you need to know is that the code between the two brace brackets `{ }` is run every time a new entity is spawned on the tabletop. This just gives us an easy way of running your code when we're in the tabletop.

## Compile and Run

To run this code, we must first compile it. Go into Quest Sage's main menu and click Author. Then, select your resource bundle and click Compile. When you click this button, Quest Sage analyses your code and converts it into a format that it can load on a tabletop.

You can now make a new single player game in Quest Sage and enable your resource bundle. Whenever you create a new entity, it should print the text "Hello, World!" to the screen and the log file.

