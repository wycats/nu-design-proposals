# Inline Function Syntax

Functions can be defined inline.

### Arrows

The most basic inline function is `-> [PARAMS] { [BODY] }`

```haskell
ls |> where -> ($file) { compare { $file.type == Dir } }
```

### `$it` Shorthand

An inline function that declares no arguments desugars into an inline function with a single argument. Inside the block, `$it` refers to that argument.

```haskell
ls |> where -> { compare { $it.type == Dir } }

-- using `=` shorthand, the above is equivalent to

ls |> where -> {= $it.type == Dir }
```

### Comparison Shorthand

Finally, when a function or method is invoked directly, and one of its formal parameters has the shape of a [Predicate](block-syntax.md#predicate-function), a further shorthand block is allowed in that position.

```haskell
ls |> where type == Dir
```

A shorthand block is:

1. a column path
2. a comparison operator
3. an arbitrary expression

It expands to a function taking a single parameter. It then traverses the value of that parameter with the column path and compares it to the right hand side.

{% hint style="warning" %}
This shorthand only works when the type of the parameter in question is known to be a [Predicate](block-syntax.md#predicate-function) at parse time. For 1.0, this will only happen when invoking an imported or built-in function directly. In practice, this is sufficient for all of the cases where we currently use the shorthand.
{% endhint %}

#### Predicate Function

```haskell
type Predicate[T] = def(T) -> Boolean
```

