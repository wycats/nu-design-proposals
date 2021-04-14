# Function Definitions

```elixir
def ls(
  [Glob $path]        # a path to get the directory contents from
  --$all (-a)         # Show hidden files
  --$long (-l)        # List all available columns for each entry
  --$short-names (-s) # Only print the file names and not the path
  --$du (-d)          # Display the apparent directory size in place
                      # of the directory metadata size
) yields File {
  # body
}
```

### Usage Comments

Any number of uninterrupted line comments immediately after a parameter specify the usage of that parameter.

Any number of uninterrupted line comments immediate before a function definition specifies the usage of that function.

### Positional Parameters

`[Glob $path]` is a parameter.

`$path` is the name of the parameter. `Glob` is its type. The wrapping `[ ... ]` makes it optional.

{% hint style="warning" %}
In parameter position, the next token must be one of:

* a flag \(starts with `--`\)
* a variable name \(starts with `$`\)
* a type \(starts with a capital letter\)

If a parameter is surrounded by `[` and `]`, it is optional. Switches \(flags with no type specified\) are always optional: if they are left out, their value is `$false`
{% endhint %}

### Named Parameters \(Flag\)

`--$all (-a)` is a named parameter, or _flag_.

`$all` is the name of the parameter. Since it does not specify a type, its type is `Switch`, which makes it optional.

### Yields

A function can specify that it yields rows, and specify the type of those rows.

`yields File` specifies this function yields rows of the type `File`.

### Returns

A function can specify a type of value that it returns via`-> Type`.



