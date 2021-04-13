# Phase 1: Reading

The reading phase breaks the source code into a token tree.

* Imports
* Atomic \(leaf node\)
* Grouped \(surrounded by paired delimiters\)

Imports are processed in the reading phase. The [expanding phase](phase-2-expanding/) may not expand any syntax into additional imports.

Atomic tokens are tokens like string literals, variable references, comments and generic words.

Grouped tokens are surrounded by:

* `[` and `]`
* `(` and `)`
* `{` and `}`

{% hint style="info" %}
The reading phase is **not** semantic. This means that identifiers, keywords, file name and column paths are all parsed as "words" to be processed by the expansion algorithm.  
{% endhint %}

