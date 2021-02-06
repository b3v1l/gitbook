# NoSQL Injection

## NoSQL Injection

* NoSQL Types = MongoDB,Couch
* Unstructured data
* Grows Horizontally
* Injection Usualy happens when :

  ```text
  • the endpoint accepts json data in the request.
  • we are able to manipulate the query using NoSQL comparison operators.
  ```

* Operator greater than Null :

`[{"$gt":""}]`

```text
> Greater than = $gt
< Less than = $lt
>= greater than equal = $gte
<= less than equal = $lte
```



### Resources

{% embed url="https://github.com/swisskyrepo/PayloadsAllTheThings/" %}

{% embed url="https://blog.websecurify.com/2014/08/hacking-nodejs-and-mongodb.html" %}











