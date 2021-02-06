# jq

## jq

Get one specific field and add the values \(if int ...\)

```text
cat file.json |  jq '.[] | .THEFIELD' | awk '{sum+=$0} END{print sum}'
```

Get a specific value in a specific field

```text
cat file.json | jq '.[] | select(.MY_FIELD == 393)'
```

\`\`

