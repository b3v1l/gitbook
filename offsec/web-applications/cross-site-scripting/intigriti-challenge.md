# Intigriti Challenge

## Challenge no Burp

[https://challenge.intigriti.io/](https://challenge.intigriti.io/)

1\) **Inspector Tab**

* Check Sources for files \(here index and script.js\)

2\) **Network Tab**

* Apps is using a CSP \(Content-Security-Policy\) used as a protection against XSS

![](../../../.gitbook/assets/597bb3301b4c471ca873607d847f5687.png)

[https://csp-evaluator.withgoogle.com/](https://csp-evaluator.withgoogle.com/) = CSP Evaluator allows developers and security experts to check if a Content Security Policy \(CSP\) serves as a strong mitigation against cross-site scripting attacks.

![](../../../.gitbook/assets/85da28e9633f46a0a295539e12cafa66.png)

* In that case, default-src means that any JS file hosted on the server will be executed.

3\) **Console tab**

```text
var jsLocation = "https://challenge.intigriti.io/script.js";
undefined
var cspBypass = `<script src="${jsLocation}"></script>`;
undefined
document.write(cspBypass);
```

We can confirm that js will work if it's loaded using a server resource \(js file\)

4\) **Dynamic content**

We only dynamic content of the website is the following menu :

![](../../../.gitbook/assets/e379a9c17b974aa484f4ed0a40ad1b91.png)

![](../../../.gitbook/assets/9397a9976f0242979c866e289482a45f.png)

Back in Element Tab, we can check what is it all about :

![](../../../.gitbook/assets/2861888002e649cc979dda1e03fdcfb2.png)

* 1 to 6, what about 7 ? :\) `https://challenge.intigriti.io/#7` 

![](../../../.gitbook/assets/e1871f3fe4494a9f8b54726237453344.png)

* Check for reflexion : `https://challenge.intigriti.io/#7polo`

![](../../../.gitbook/assets/969c8e97ace442f29fb320f99f39455d.png)

**Test injection** `https://challenge.intigriti.io/#7polo<script%20src=script.js>`

![](../../../.gitbook/assets/f12bf74a4caf406b8b4568178ad305cc.png)

* Network tab 

404 strange error

![](../../../.gitbook/assets/1f6171cc2d2c460ab12773e87f1a1172.png)

* Copy paste the error output in the console \(weird but it's javascript\)...

![](../../../.gitbook/assets/8b57233801e7438e9e545451439ed812.png)

Inject Quotes :

![](../../../.gitbook/assets/8f42d3c6190946d1a2a457c85a12cde1.png)

But no error with double quotes.

Inject int and quote :

`https://challenge.intigriti.io/#7polo'+404+'`

![](../../../.gitbook/assets/4dedd7c3ef1a4ff4b10057e655a44863.png)

* Inject alert script :

  `https://challenge.intigriti.io/#7polo'-alert(document.domain)+'`

![](../../../.gitbook/assets/9abecd51c0334129896601f0d13aa5c0.png)

Self XSS by CSP bypassed :

![](../../../.gitbook/assets/a98ce885e5d147878c72b41555b5fed6.png)

![](../../../.gitbook/assets/40e9babec0104d09be22bf664dfca30e.png)

