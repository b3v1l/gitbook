# swaks

## swaks

### Install

```text
pacman -S swaks
```

### Usage

```csharp
for email in $(cat /home/b3v1l/emails.txt);
do
    swaks \
        --from santa.claus@cloud.local \
        --to $email \
        --header 'Subject: Naughty holidays' \
        --server x.x.x.x
done

```

```csharp
swaks --to someone@tld.com --from "me@sefnet.local" --header "Subject: Test mail" --body "This is a test mail" --attach-type application/zip --attach file.zip --server smtp.sefnet.local --port 587 --timeout 40s --auth LOGIN --auth-user "me@sefnet.local" --auth-password "MyPassword" -tls
```

#### HTML content

```csharp
 --attach-type text/html --attach @index.html
```

### Embedded link

```csharp
swaks  -t user@target.com --server  <SERVER_IP> --attach-type text/html --attach-body @index.html
```

