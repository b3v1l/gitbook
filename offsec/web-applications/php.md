# PHP

## PHP

### Interactive shell

```text
php -a
```

### Execute

```text
php -f file.php
```

### Comparison

Can be used to trick the frontend ...

* **Strict comparisons with `===`**

```csharp
php -a                                                                                            ─╯
Interactive shell

php > var_dump(1===1);
bool(true)
php > var_dump(1==='1');
bool(false)
php > 

```

* **Loose comparisons with `==`**

```csharp
php > var_dump(1==1);
bool(true)
php > var_dump(1=='1');
bool(true)
php > var_dump(1=='1abcd');
bool(true)
php > var_dump(1=='1abcssssssssssssssd');

```

### Deserialization

```text
<?php
class Exploit
{
   private $hook = "phpinfo();";
}
print urlencode(serialize(new Exploit));
?>

```

