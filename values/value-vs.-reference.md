# Value vs. Reference

### Value Semantics

In Nu, a type has _value semantics_ if it has no interior mutability and no associated finalizers.

{% hint style="info" %}
Interior mutability is a recursive property. A type has interior mutability if any of its component parts have interior mutability.
{% endhint %}

When a type has value semantics in Nushell:

* it can be freely cloned, serialized and shared
* it is identical to: another instance of the same type with identical serialization
* it is equivalent to: anything it is identical to

### Reference Semantics

In Nu, a type has _reference semantics_ if is it possible to distinguish two structurally identical instances.

{% hint style="info" %}
The only ways in which two structurally identical instances can be distinguished are:

* At least one of the instances has interior mutability, so it is possible to observe that the structure of the two instances changes over time.
* The type has at least one associated finalizer that has [side-effects](value-vs.-reference.md#side-effects-and-purity)
{% endhint %}

When a type has reference semantics in Nushell:

* it may be **moved**, **shared** or **leased**
* it specifies a Structural Value 
* it is identical to: an object with the same Object Identity as this object
* it is equivalent to: another instance of the same type with an identical [Structural Value](value-vs.-reference.md#structural-value).

#### Structural Value

The _Structural Value_ of a reference type is a list of internal slots that, together, represent the structure of the type.

A type's _Structural Value_ may include other reference types, but the computed structural value of a type recursively determines the Structural Value unless the only components are [value types](value-vs.-reference.md#value-semantics). 

