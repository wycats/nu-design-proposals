# Function Definitions

```elixir
def ls(
  Glob [$path]        # a path to get the directory contents from
  --$all (-a)         # Show hidden files
  --$long (-l)        # List all available columns for each entry
  --$short-names (-s) # Only print the file names and not the path
  --$du (-d)          # Display the apparent directory size in place
                      # of the directory metadata size
) yields File
```

### `Glob [$path]`





