# Escaped String Interpolation into dynamic inline Javascript

## Escaped String Interpolation into dynamic inline Javascript

* **We are in a script tag . This is escaped string interpolation but it's vulnerable.**

We dont even need to use the tag `<script>`

`var user3 = #{name3}`

* so we are in 

```text
<script>
<p> no result for [escaped value user input] </p>
</script>
```

* we can just use  1;alert\(1\);

![](../../../../.gitbook/assets/34c8b649bb17478fbc757c0e7224143f.png)

![](../../../../.gitbook/assets/18c4018bb9fd464fb84d0fb5834921b6.png)

* Mitigation :

```text
var user3 = “#{name3}” and not #{name3}
```

