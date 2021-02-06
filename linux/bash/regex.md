# Regex

## Regex examples

```text
. = any single chars
^ = start of the string
$ = end of string

\d = any digits
\D = any non digits
[0-9] = \d
[^0-9] = \D
\s = whitespace
\S = non whitespace
'+'' = one or more preceding
'*' = zero or more preceding
```

![](../../.gitbook/assets/e8e32279913d47e9af96a03540a68a47.png)

### Hex serial number example

```text
XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX
```

`[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}`

### Resources

{% embed url="https://gchq.github.io/CyberChef/" %}

{% embed url="https://regexr.com/" %}

{% embed url="https://regex101.com/" %}











