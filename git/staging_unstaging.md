
## Stagging

### Stagging a single file
```bash
git add <filename>
```
Example:
```bash
git add myfile.txt
```

### Stagging multiple files
```bash
git add <file1> <file2> <file3>
```

Example:
```bash
git add file1.txt file2.txt
```
### Stage all changes in the current directory
```bash
git add .
```

### Stagging changes in a specific directory
```bash
git add <directory>
```
Example:
```bash
git add src/
```

## Unstaging

### Unstage a single file
```bash
git restore --staged <filename>
```
Example:
```bash
git restore --staged file1.txt
```

### Unstage multiple files
```bash
git restore --staged <file1> <file2> <file3>
```
Example:
```bash
git restore --staged file1.txt file2.txt file3.txt

```

### Unstage files in specific directory
```bash
git restore --staged directory
```
Example:
```bash
git restore --staged src/
```

### Unstage all files
```bash
git restore --staged .
```
