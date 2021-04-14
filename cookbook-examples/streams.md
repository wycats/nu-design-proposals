# Streams

A stream is a built-in Reference Class with a number of build-in methods.

```haskell
class(reference) Stream[T] {
  implements Clone

  data opaque
  
  def skip!(
    Integer $rows -- How many rows to skip
  ) mutates self
  
  def skip! until(
    Fn(T) -> Boolean
  ) mutates self

  def skip! while(
    Fn(T) -> Boolean
  ) mutates self

  
  def compact!() mutates self
}
```

### Reference Classes

A reference class is like a normal class, but it can have [_effectful methods_](streams.md#effectful-methods-ending-with).

An effectful method's name ends in `!` and specifies the reason it is effectful.

{% hint style="info" %}
Reference classes are expected to be rare. At the moment, the only reference types that this proposal exposes are `List` and `Stream`. For now, there is no user-exposed way to create reference types.
{% endhint %}

### The `opaque` data modifier

The `opaque` modifier is only allowed in data definitions for externally implemented types.

### Effectful Methods \(ending with `!`\)

Methods that end with `!` are effectful in one of the following ways:

* mutates self \(modifier: `mutates self`\)
* mutates self.column \(when data is not opaque, modifier: `mutates self.column-name`\)

An effectful method may only be called by code that has a unique reference to the object.

{% hint style="warning" %}
This proposal doesn't currently propose a syntax for sharing a reference with another function, but functions that share a reference may not call its effectful methods.
{% endhint %}



