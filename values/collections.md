# Collections

### Row

{% tabs %}
{% tab title="Description" %}
{% hint style="info" %}
A row is a dictionary of labelled values. Each value may have an optional type.
{% endhint %}

The _label_ in a row is a [Symbol Path](semantics_primitives.md#proposal-column-path-symbol-path).

Rows have [Value Semantics](value-vs.-reference.md#value-semantics).

A row may have an associated [class](classes-and-instances.md#class), which specifies its [methods](classes-and-instances.md#method).
{% endtab %}

{% tab title="Slots" %}
| Slot Name | Type |
| :--- | :--- |
| `@entries` | `:some[:code/Row]` |
| `@class` | optional `:code/Class` |
{% endtab %}

{% tab title="Aliases" %}
* Object \(JS\)
* Hash \(Ruby\)
* Dictionary \(Python\)
* Associative Array \(PHP\)
{% endtab %}
{% endtabs %}

### List

{% tabs %}
{% tab title="Description" %}
{% hint style="info" %}
A list contains a number of values
{% endhint %}

A List of Rows is a table.

Lists are [Streams](streams.md), and have [Reference Semantics](value-vs.-reference.md#reference-semantics).
{% endtab %}

{% tab title="Aliases" %}
* Array
* Tuple
* Stream
{% endtab %}
{% endtabs %}

### Table

{% tabs %}
{% tab title="Description" %}
{% hint style="info" %}
A table is a [List](collections.md#list) of [Rows](collections.md#row).
{% endhint %}

Tables are [Streams](streams.md), and have [Reference Semantics](value-vs.-reference.md#reference-semantics).

A Table may be finite or infinite.
{% endtab %}

{% tab title="Aliases" %}
* Stream
* Table
* Array of Dictionaries
{% endtab %}
{% endtabs %}



