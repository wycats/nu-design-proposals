# Signature

### Function Signature

A [Function](../values/functions.md)'s Signature defines its interface.

| Slot Name | Type | Description |
| :--- | :--- | :--- |
| `@name` | `:String` | The name of the function |
| `@usage` | `:String` | A usage string |
| `@positional` | `:List[:Type]` | A list of the types of positional arguments |
| `@rest` | `:Type` | The type of the rest argument \(List of `T`\) |
| `@named` | `Table[:code/Column, :Type]`  | The types of named arguments, as a finite Table |
| `@input` | `:some[:code/Row]` | The type of each row of input data |
| `@yields` | `:some[:code/Row]` | The type of each row of yielded data |
| ℹ  `@returns` | `:Type` | The return type of the function |

### Method Signature

A [method](../values/classes-and-instances.md#method) signature \(`:code/MethodSignature`\) is a [Function Signature](signature.md#function-signature) with one additional slot:

| Slot Name | Type | Description |
| :--- | :--- | :--- |
| `@self` | `:Type` | The `:Type` must be a [class](../values/classes-and-instances.md#class). |

