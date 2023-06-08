# Python Flask application

## Python Flask application

* Eval is used and the following route is used :

`@app.route('/whatever/something')`

* We can try to break it using 'quotes or double quotes':

![](../../../.gitbook/assets/08846978fe434e5e8f4e7edc4653b71f.png)

![](../../../.gitbook/assets/2951741c48f941889961b2ad0127066e.png)

* Looking for code execution using str:

![](../../../.gitbook/assets/8a190c31a19349cd8b09f6f3f8602bf7.png)

* Response :

![](../../../.gitbook/assets/caf1df2da5d24e5b9222a86411c34705.png)

* Code execution:

&#x20;                    \* Fails

![](../../../.gitbook/assets/7de5f80878b84bb59fa10cac05e9cc7d.png)

* Success:

![](../../../.gitbook/assets/c8b988a838844b66809e55f6dad8dc52.png)

![](../../../.gitbook/assets/2fa6a6b9a7c0469db1c9d6bae18cc393.png)

![](../../../.gitbook/assets/98a74522427a42e5b14e41dc7ab6cc11.png)

![](../../../.gitbook/assets/fc288098169c4d3dbcf7bfadedbc0a9c.png)

* Bypass '/' blacklist using ding the command, ie `cat /etc/passwd`

![](../../../.gitbook/assets/d7582932bf0f4b05bf8d83b7fb1d3325.png)
