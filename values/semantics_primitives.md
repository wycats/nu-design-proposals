---
description: Nushell's Primitives
---

# Primitives

{% hint style="info" %}
All primitives have [Value Semantics](value-vs.-reference.md#value-semantics).
{% endhint %}

| 🧪 | Type | Description | [Rosetta\[1\]](semantics_primitives.md#1-rosetta-stone) | Notes |
| :--- | :--- | :--- | :--- | :--- |
|  | `:Boolean` | `true` or `false` |  |  |
|  | `:Integer` | An arbitrarily large integer | BigInt |  |
|  | `:Decimal` | An arbitrarily precise rational number | BigDecimal |  |
|  | `:String` | A sequence of UTF-8-encoded Unicode characters |  |  |
|  | `:BinaryData` | A sequence of bytes, representing binary data | ArrayBuffer |  |
|  | `:Line` | A String that should be laid out as a block | &lt;p&gt; |  |
| 🧪 | `:Symbol` | The representative of symbolic values |  | ℹ [Proposal Below](semantics_primitives.md#proposal-code-representation) |
| 🪓 | `:ColumnPath` | Representation of a path to data |  | ℹ [Proposal Below](semantics_primitives.md#proposal-code-representation) |
|  | `:GlobPattern` | The representation of a file pattern | Glob, Pattern | [Glob crate](https://docs.rs/glob/0.3.0/glob/struct.Pattern.html) |
|  | `:Date` | A date, time and time zone |  |  |
|  | `:Duration` | A length of time | Interval |  |
|  | `:Range` | A sequence of values from start to finish |  | Optionally exclusive optionally open-ended |
|  | `:FilePath` | A path to a file on the operating system | Path, Pathname |  |
|  | `:FileSize` | The size of a file in bytes |  | ℹ Proposal Below |
|  | `:Id` | The representation of identity |  | For identity in reference types |

#### \[1\] Rosetta Stone

Names for the same concept in other programming languages.

### `FilePath`

A `String` that represents a path to a file.

### ℹ **Proposal: Code Representation**

{% hint style="info" %}
This section is a proposal for primitive value types that represent code concepts. It enhances the existing _Column Path_, which represents a programmatic path to data.
{% endhint %}

#### Symbol

A _Symbol_  is a path 

###  `Column Path` ➡ `Symbol Path`

### 

