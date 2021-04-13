# Functions

A Function is a block of code with an associated interface, its [Signature](../function/signature.md).

The body of a function is a [separator](../syntax/untitled.md#separator)-delimited list of [expressions](../syntax/phase-2-expanding/expressions.md).

A function receives data via parameters \(positional, rest, and named\).

A function provides data to its caller via [yields](functions.md#yields) and [returns](functions.md#returns).

| Slot Name | Type | Description |
| :--- | :--- | :--- |
| `@signature` | `:code/Signature` | See [Signature](../function/signature.md) |
| `@body` | `:List[:code/Expression]` |  |

### Yields

While a function is evaluating, it may yield values to its output stream.

### Returns

When a function is done evaluating, it may return a value, which is not part of the output stream.

