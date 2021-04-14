# The Pipeline: Input and Output

Functions that take input and produce output on the pipeline have one of these shapes.

### The Pipeline

When a command appears in the first position in the pipeline, it is a source.

When a command appears between two `|` in the pipeline, it is a mapper or fanout mapper.

When a command appears in the final position in the pipeline, it is a sink.

### Source

```haskell
type Source[T] = def() -> yields T
```

### Sink

```haskell
type Sink[T] = def(Stream[T])
```

```haskell
def print-all(Stream[Any] $input) {
  $input | do -> ($item) { echo $item }
}

-- usage

ls | print-all
```

### Mappers

A mapper takes a single value and returns a new value.

{% hint style="info" %}
The Mapper type is a convenience to allow terse 1:1 transformations. A mappers desugars into a Fanout Mapper that yields the return value of the underlying mapper.
{% endhint %}

```haskell
type Mapper[T U] = def(T) -> U
```

```haskell
def upcase(String $value) -> String {
  str upcase $value
}

-- usage

ls | upcase
```

### Fanout Mappers

A fanout mapper takes a single value and yields zero or more values.

```haskell
type FanoutMapper[T Y] = def(T) yields U
```

```haskell
def words(String $value) yields String {
  yield all (str split $value) 
} 
```

