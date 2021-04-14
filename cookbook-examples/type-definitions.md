# Type Definitions

```haskell
export data FileType {
  | File
  | Dir
  | Symlink
  | BlockDevice (display "Block Device")
  | CharDevice  (display "Char Device")
  | Pipe
  | Socket
  | Unknown
}

export data UserId wraps Integer
export data GroupId wraps Integer

export data Permission {
  Boolean read
  Boolean write
  Boolean execute
}

export class FileMode {
  data {
    Permission user
    Permission group
    Permission others
    Boolean setuid
    Boolean sticky
  }
}

export class File {
  data {
    FilePath name
    FileType type
    FileSize size
    Date modified
  }
}

export class File(verbose) {
  data {
    [FilePath target] -- the target for symlinks

    cfg("unix") {
      Integer num_links -- the number of links
      Integer inode
      FileMode mode
      UserId uid
      GroupId group
    }
  }
}

```

### Data Definitions

Data definitions are items that begin with the keyword `data`or `class`.

A `data` definition specifies the structure of type. A `class` definition specifies _behavior_  that should be associated with instances of this type. 

### Enumeration

{% hint style="info" %}
This feature is called _enum_ in Rust, _sum type_ in Haskell and _enumeration_ in Swift.
{% endhint %}

Each line in an enumeration begins with `|`.

### Row

{% hint style="info" %}
This feature is called _struct_ in Rust, _product type_ in Haskell, and _structure_ in Swift.
{% endhint %}

Each line in an enumeration begins with a `|` followed by one of:

* An uppercase letter \(a type\)
* A lowercase letter \(a variant\)

### Wrapping Types

It is possible to create a type that simply wraps another type.

This is sugar for creating a structure with:

* the same columns
* plus an `id` column that represents the data type \(`Nu/ID`\)
* a constructor that takes the fields as arguments, and adds  the `id`

Using a unique `id` column for the data type makes wrapping types _structurally equal_ to other instances of the same wrapping type.

### Classes

A class combines a data definition with behavior that interacts with that data.

{% hint style="info" %}
By default, a class is read-only, and its columns are immutable. These kinds of classes have [Value Semantics](../values/value-vs.-reference.md#value-semantics).
{% endhint %}

### Reference Classes

{% hint style="danger" %}
The semantics of Reference Classes are necessary in order to explain [Streams](streams.md). In 1.0, there will be no user-facing syntax in NuLang for creating reference classes, mutating fields or defining destructors. 
{% endhint %}

A hypothetical example.

```haskell
class(reference) Point {
  data {
    Integer x
    Integer y
  }
  
  def incr-x() mutates x {
    self.x <- math { self.x + 1 } 
  }
}
```

Reference classes are specified 

