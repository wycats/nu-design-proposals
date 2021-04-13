# Classes and Instances

### Class

{% hint style="warning" %}
A Class is a _type_. It has a shape for its data, and a dictionary of methods.
{% endhint %}

| Slot Name | Type | Description |
| :--- | :--- | :--- |
| `@name` | `:String` |  |
| `@shape` | `:code/Row` | The representation of a row |
| `@methods` | `:Table[:code/Column, :code/Method]` | A table of methods |

### Method

A method is a function with one additional slot:

| Slot Name | Type |
| :--- | :--- |
| `@class` | `:code/Class` |

When a method is called, its reserved `$self` variable is populated with an [instance](classes-and-instances.md#instances) of the class.

### Instances

An instance of a class is a row with the class as its associated class.

