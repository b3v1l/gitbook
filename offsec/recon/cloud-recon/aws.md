# AWS

## Get AWS Access key from your account : <a id="get-aws-access-key-from-your-account"></a>

[https://console.aws.amazon.com/iam/home?region=eu-west-3\#/security\_credential](https://console.aws.amazon.com/iam/home?region=eu-west-3#/security_credential)

### **Install awscli**

`apt-get install awscli`

### **Configure your creds**

`root@thp3:/opt/bucket_finder# aws configure`  
 AWS Access Key ID \[None\]:

### **Enumerate remote share**

`root@thp3:/opt/bucket_finder# aws s3 ls s3://cyberspacekittens PRE secrets/2`8-02-04 15:42:58 25 ignore.txt

### **Get permissions** 

`root@thp3:/tmp# aws s3api get-object-acl --bucket cyberspacekittens --key ignore.txt`

```bash
{                                                                                                                                                                                          
    "Owner": {                                                                                                                                                                             
        "DisplayName": "secure",                                                                                                                                                           
        "ID": "3bb06f3f5202dee0a434398b93cee264b501d89b3935e38f656182488cd2fb9a"                                                                                                           
    },                                                                                                                                                                                     
    "Grants": [                                                                                                                                                                            
        {                                                                                                                                                                                  
            "Grantee": {                                                                                                                                                                   
                "Type": "Group",                                                                                                                                                           
                "URI": "http://acs.amazonaws.com/groups/global/AllUsers"                                                                                                                   
            },                                                                                                                                                                             
            "Permission": "READ"                                                                                               
```

