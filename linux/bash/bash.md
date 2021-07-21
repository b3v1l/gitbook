# awk

## Usage

### Remove tab

```csharp
awk -F\t '{print $1}'
```

### print lines with size greater or equal to 1000

```csharp
cat access.log  | awk 'length>=1000' 
```

### Print line where bytes size are greater or equal to 1000

```csharp
cat access.log  | awk '$10 >= 1000' 
```

### Print results depending on the length

```csharp
awk 'length($0) > 7' /etc/shells 
```

### Add tab in the output

```csharp
awk -F":" '{print $1"\t"$2"\t"$3}' /etc/passwd  
```

### Replace field separators

```csharp
awk 'BEGIN{FS=":";OFS="-"} {print $1,$6,$7}' /etc/passwd | head -n 3
```

### Search for a separator and print the last column

```csharp
 awk -F "/" '/^\// {print $NF}' /etc/shells  
```

### If statements

```csharp
# if last field = zsh => print
ps -ef | awk '{ if($NF == "/bin/sh") print $0}'
```

### Print every lines starting at char number 4

```csharp
awk '{print substr($0, 4)}' myfile.txt
```

#### random example

```csharp
awk '{print $8}' file | cut -d '=' -f2 | sort | tail | ORACLE\Administrator (RID: 500) cat enum_users.txt |awk '/RID/ {print $2} '  
```

\`\`

