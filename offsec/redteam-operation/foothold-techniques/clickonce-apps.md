# ClickOnce Apps

## ClickOnce Apps

* Create a C# console application
* Publish the code in virtual studio (as an Admin)
* The application is dropped on the disk (artifact) as a temp file into the folder C:\Users\\%Username%\AppData\Local\Apps\2.0\RANDOM\_LETTER
* Use "only available online" to minimize artifact on the disk (or it will create an entry in the startup menu and add few register keys !)

### Publish and Sign the app

![](<../../../.gitbook/assets/image (61).png>)

* Sign the App (using Admin account, Create Test Certificate)

![](<../../../.gitbook/assets/image (37).png>)

![](<../../../.gitbook/assets/image (22).png>)

* Publish the app (select online only)

![](<../../../.gitbook/assets/image (26) (1).png>)

![](<../../../.gitbook/assets/image (241).png>)

* Host the files on a webserver

![](<../../../.gitbook/assets/image (119).png>)
