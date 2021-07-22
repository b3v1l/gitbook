# xargs

## Usage

### Create 10 files

```csharp
seq 10 | xargs -I {} touch {}
```

### Rename files

```csharp
ls -lh | cut -d " " -f9 | xargs -I {} mv {} {}.txt 
```

### find and xargs

```csharp
find . -iname "*.txt*" -type f | xargs rm 
```

