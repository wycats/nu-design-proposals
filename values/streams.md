# Streams

At present, streams are the only [reference types](value-vs.-reference.md#reference-semantics) in Nushell.

### Class Definition

#### Shape

| Slot Name | Type |
| :--- | :--- |
| `@id` |  |

#### Methods

```elixir
class(reference) Stream[T] {
  shape {
    [[opaque]]
  }

  skip(
    mutates self,
    [:Int $rows] # How many rows to skip
  ) -> :Stream[T]
}
```



