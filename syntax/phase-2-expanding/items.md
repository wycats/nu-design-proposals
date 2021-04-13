# Items

The top-level expander iterates over a stream of reader tokens.

In each iteration, the expander identifies an in-scope macro name and delegates to the macro, which must produce zero or more items.

### Standard Macros

| Name | Semantics |
| :--- | :--- |
| `def` | Define a method |
| `class` | Define a class |
| `const` | Define a constant value |

