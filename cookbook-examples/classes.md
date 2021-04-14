# Classes

### Overloading

A method name can be repeated multiple times in a class if an overload parameter is specified, and all of the overloaded methods with the same name are statically disjoint.

{% hint style="warning" %}
At the moment, the only kind of supported overload is overload :symbol, which the [Subcommand syntax](classes.md#subcommands) desugars to.
{% endhint %}

```haskell
class Git {
  def bisect(
    overload :start
    [String $bad]
    [String $good]
  )
  
  def bisect(
    overload :good
  )
  
  def bisect(
    overload :bad
  )
}
```

This makes `(git bisect start)` work, as well as `(git bisect good)` and `(git bisect bad)`.

### Subcommand Shorthand

There is a shorthand for overloads that model subcommands: if a method's name is followed by another identifier instead of `(`, that name is a _subcommand_ of the parent method.

```haskell
class Point {
  data {
    Integer x
    Integer y
  }
  
  def incr x() -> Point {
    Point { x: $self.x + 1, y: $self.y }
  }
  
  def incr y() -> Point {
    Point { x: $self.x, y: $self.y + 1 }
  }
}
```

This desugars to:

```haskell
class Point {
  data {
    Integer x
    Integer y
  }
  
  def incr(overload :x) -> Point {
    Point { x: $self.x + 1, y: $self.y }
  }
  
  def incr(overload :y) -> Point {
    Point { x: $self.x, y: $self.y + 1 }
  }
}
```

#### Additional Sugar: Grouping

There is additional sugar for defining subcommands together.

```haskell
class Point {
  data {
    Integer x
    Integer y
  }
  
  def incr {
    x() -> Point {
      Point { x: $self.x + 1, y: $self.y }
    }
  
    y() -> Point {
      Point { x: $self.x, y: $self.y + 1 }
    }
  }
}
```

