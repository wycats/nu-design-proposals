# Baseline Expressions

When the expander is in the "expression" state.

| Next Token `token` is | Then: |  |
| :--- | :--- | :--- |
| Grouped by `(` ... `)` | parse a call expression |  |
| An `->` | parse an inline function expression |  |
| A variable reference `$ID` | emit \` |  |
| A literal | emit `T` |  |
| A word | emit a file path for that word |  |



