# Dom XSS

## DOM XSS

Dom XSS = Client side XSS or JS XSS

### Listeners

From the source file, we can check Global Listeners

![](../../../.gitbook/assets/033953c53d50422785107a5ed0a7c9a1.png)

From Global Listener, search **"message"**

![](../../../.gitbook/assets/e7a6723ef6bb426cb03946df1fbd14fc.png)

Set a break point in the code and use the console to post something random using window.PostMesage\('message', 'target origin'\)

![](../../../.gitbook/assets/bddd65ab461d4d5cad36f863eab6185c.png)

### Example \(Firing range [https://public-firing-range.appspot.com/](https://public-firing-range.appspot.com/)\)

Set up a postmessage and a break point in the debugger

![](../../../.gitbook/assets/958ef3f6ef994a00ba8cac3b0f95b1f4.png)

Set a new value to content and release the break point

![](../../../.gitbook/assets/3e45cc18c07c4b36924b5fb07eb65255.png)

![](../../../.gitbook/assets/b15b6593965f4fd2937d6c937cc4e995.png)

XSS but there is nothing to steal \(httponly mitigation and Same Origin Policy, which deny javascript getting executed from other domains\).

* Element is giving the current view of the HTML code which has been manipulated by javascript

### ComplexMessageDocumentWriteEval

![](../../../.gitbook/assets/7dd8b33e4d794e75acd4b248b3b1eeb1.png)

From the code, msg \(the input\) is waiting to for data and action:

* window.postmessage

![](../../../.gitbook/assets/9d097c68dacc4f9cbe613e2689e5d4e0.png)

### POC using repl.it------------- TODO

### Examples

![](../../../.gitbook/assets/f40e6fbf5a294d719030780655435597.png)

![](../../../.gitbook/assets/7daa21ad5f4b463abe64eb4d680f388b.png)

![](../../../.gitbook/assets/e772d2cebb534a549dbd2d5a27620126.png)

`http://vulnerable.site/index.php#%3E%3Cscript%3Ealert(1)%3B%3C%2Fscript%3E`

