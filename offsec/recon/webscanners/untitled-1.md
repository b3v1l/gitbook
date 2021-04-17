# wfuzz

## wfuzz usage <a id="wfuzz"></a>

{% embed url="https://github.com/xmendez/wfuzz" %}

```text
wfuzz -c -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -H "User-Agent: SomethingNotObivousforWAF" --sc="500,403,301,302,204,400" "http://10.10.10.69/?FUZZ='"
```

Warning: Pycurl is not compiled against Openssl. Wfuzz might not work correctly when fuzzing SSL sites. Check Wfuzz's documentation for more information.

* Wfuzz 2.2.9 - The Web Fuzzer 

Target: [http://10.10.10.69/syncFUZZ](http://10.10.10.69/syncFUZZ)'  
 Total requests: 118

## ==================================================================  ID Response Lines Word Chars Payload <a id="id-response-lines-word-chars-payload"></a>

000082: C=403 7 L 10 W 175 Ch "?x=&gt;"  
 000083: C=403 7 L 10 W 175 Ch "?x=\|"

Total time: 1.429419  
 Processed Requests: 118  
 Filtered Requests: 116  
 Requests/sec.: 82.55096

--hc argument to hide status codes \(so for example, --hc=404 will hide all directories/files that aren't found\) or --sc to only show certain ones \(so --sc=200 for all URLs that return a 200 status\)

I generally prefer to blacklist uninteresting status codes, as only showing certain ones can result in a lot of missing information  
 500, 403, 301, 302, 204, 400 etc are all potentially interesting status codes other than 200  
 10:22 PM404 is rarely interesting though

