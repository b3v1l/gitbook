# sed

## Usage

### search and replace a string

```csharp
 sed 's/polo/perin/' < file > newfile
```

```csharp
sed -i 's/polo/perin/g' file 
```

### multiple replacements

```csharp
head -n 4  /etc/passwd | sed -e 's/root/polo/g' -e 's/bin/bim/g'
```

### remove empty lines

```csharp
 cat /etc/appstream.conf | sed '/^$/d' 
```

### remove empty lines and commented lines

```csharp
cat /etc/appstream.conf | sed -e '/^$/d' -e '/^#/d'
```

### separator

```csharp
sed 's#/#\n#g' file.txt 
```



