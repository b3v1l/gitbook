# jq

## jq

Get one specific field and add the values (if int ...)

```
cat file.json |  jq '.[] | .THEFIELD' | awk '{sum+=$0} END{print sum}'
```

Get a specific value in a specific field

```
cat file.json | jq '.[] | select(.MY_FIELD == 393)'
```

