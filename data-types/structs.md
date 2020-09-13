# Structs

You can create your own data types to store related data. For example, a character might have a health value, an armour value and a name to display. Name your data structure by writing `struct` then the name of your new data type.

```text
struct Character {
    health: Int
    armour: Int
    name: String
}
```

To create an instance of this data type \(a variable whose type is `Character`\), use the syntax `new Character`.

```text
let character = new Character {
    health = 10;
    armour = 2;
    name = "Jeff";
};
```

You can get and set the fields of this struct by using a dot `.` to address the name of the field. For example:

```text
character.name = "New name here";
let hp = character.health;
hp.print();
```



