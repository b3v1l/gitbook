# awk

## Awk

### Usage

#### Remove tab

```text
awk -F\t '{print $1}'
```

#### print lines with size greater or equal to 1000

```text
cat access.log  | awk 'length>=1000' 
```

#### Print line where bytes size are greater or equal to 1000

```text
cat access.log  | awk '$10 >= 1000' 
```

#### random example

```text
awk '{print $8}' file | cut -d '=' -f2 | sort | tail | ORACLE\Administrator (RID: 500) cat enum_users.txt |awk '/RID/ {print $2} '  
```

\`\`

