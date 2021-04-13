# Unifying Functions

### Problems

* How does input and output compose?
* What does `$it` desugar to
* How are [yielded values](https://github.com/nushell/nushell/blob/main/crates/nu-protocol/src/signature.rs#L119) represented

### Solution

#### Semantics

A function signature is:

| Slot Name | Description |
| :--- | :--- |
| `@name` | The name of the function |
| `@usage` | A usage string |
| `@positional` | A list of the types of positional arguments |
| `@rest` | The type of the rest argument \(List of `T`\) |
| `@named` | The types of named arguments, as a finite Table |
| `@input` | The type of each row of input data |
| `@yields` | The type of each row of yielded data |
| ℹ  `@returns` | The return type of the function |

#### Syntax

```elixir
"def" [ID] "(" WS? "$in" WS? "=" ")" (WS "yields" Type)? (WS "->" Type)?

InType = "$self"

Type ::= [EXTERNAL]
Flag ::= "--" [ID] (":" WS? Type)

Positional ::= interleave(Type, WS)
Named ::= interleave(Flag, WS)
```

#### Example

```elixir
import { Glob FilePath FileSize Boolean Date } from "std:types"

variants FileType {
  File
  Dir
  Symlink
  #display "Block Device"
  BlockDevice
  #display "Char Device"
  CharDevice
  Pipe
  Socket
  Unknown
}

row File {
  | name     | type      |
  | -------- | --------- |
  | name     | FilePath |
  | type     | FileType |
  | [target] | FilePath |
  | readonly | Boolean  |
  | size     | FileSize |
  | created  | Date     |
  | accessed | Date     |
  | modified | Date     |
}

def ls(
  Glob [$path]       # a path to get the directory contents from
  --$all (-a)         # Show hidden files
  --$long (-l)        # List all available columns for each entry
  --$short-names (-s) # Only print the file names and not the path
  --$du (-d)          # Display the apparent directory size in place
                      # of the directory metadata size
) yields File
```

