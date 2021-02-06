# Bucket recon

## Slurp tool

{% embed url="https://github.com/bbb31/slurp.git" %}

`git clone https://github.com/bbb31/slurp.git` 

`/opt/slurp && cd /opt/slurp && cp /root/go/bin/slurp /opt/slurp/`

## Bucket Finder <a id="bucket-finder"></a>

`root@thp3:/opt/bucket_finder# echo cyberspacekittens > list.txt`  
 `root@thp3:/opt/bucket_finder# ./bucket_finder.rb --region us list.txt --download`

```bash
Bucket cyberspacekittens redirects to: cyberspacekittens.s3.amazonaws.com
        Bucket Found: cyberspacekittens ( cyberspacekittens.s3.amazonaws.com/cyberspacekittens )
                <Downloaded> http://cyberspacekittens.s3.amazonaws.com/ignore.txt
                <Private> http://cyberspacekittens.s3.amazonaws.com/secrets/
                <Downloaded> http://cyberspacekittens.s3.amazonaws.com/secrets/password.txt
root@thp3:/opt/bucket_finder#
```

