# Receiver Style

Functions can be written in normal style or receiver style. With receiver style, the first parameter of the function is named `this`, and it is written before the function name when called.

{% tabs %}
{% tab title="Normal Style" %}
```text
func do_stuff(left: Int, right: Int) -> Int {
    return left + right;
}

func main() {
    let a = do_stuff(1, 2);
}
```
{% endtab %}

{% tab title="Receiver Style" %}
```
func do_stuff(this: Int, right: Int) -> Int {
    return left + right;
}

func main() {
    let a = 1.do_stuff(2);
}
```
{% endtab %}
{% endtabs %}

It is largely a choice up to the programmer to choose which style to write a function in. Receiver style functions have connotations of "acting on" the receiver, and normal style functions apply equal weight to all parameters. There is no semantic difference between the function types.

However, certain specific language features require the use of receiver style functions, or forbid the use of receiver style functions. You will see this more as you use more features of the language.

{% hint style="danger" %}
You cannot call a normal style function in receiver style, or vice versa.
{% endhint %}

