
# Neovim Replace Command

## Syntax:
```
:%s/old_pattern/new_pattern/flags
```

### Components:
- `:%s` – Start the substitution command across the entire file.
- `old_pattern` – The text or pattern you want to replace (supports regular expressions).
- `new_pattern` – The text you want to replace the old pattern with.
- `flags` – Optional flags to modify the behavior of the substitution.

## Common Flags:
- `g` – Replace **all** occurrences on each line (global replacement).
- `c` – **Confirm** each replacement (you'll be prompted to confirm before each replacement).
- `i` – Case-insensitive search (use with `g` or `c` for global/confirm replacements).
- `n` – Show the number of replacements made without actually replacing anything.
  
## Examples:

1. **Replace "foo" with "bar" globally in the file:**
   ```
   :%s/foo/bar/g
   ```

2. **Replace "foo" with "bar" on the current line only:**
   ```
   :s/foo/bar/
   ```

3. **Replace "foo" with "bar" globally, but ask for confirmation:**
   ```
   :%s/foo/bar/gc
   ```

4. **Case-insensitive replacement:**
   ```
   :%s/foo/bar/gi
   ```

5. **Show number of replacements without actually making changes:**
   ```
   :%s/foo/bar/n
   ```

## Visual Mode Replacement:
- You can also use the `:s` command in visual mode to replace text within a selected area.
  1. Enter Visual Mode (`v` or `V`).
  2. Select the text you want to replace.
  3. Press `:` and type the replacement command (e.g., `s/foo/bar/g`).

## Notes:
- Neovim supports regular expressions in the `old_pattern` and `new_pattern` sections.
- You can use `
` in the `new_pattern` to reference captured groups from the `old_pattern`.

## Further Reading:
- `:help :s`
