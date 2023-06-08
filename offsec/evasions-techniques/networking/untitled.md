# Domain fronting

## Domain fronting

{% embed url="https://b3v1l.gitbook.io/offensive-security-and-other-stuff/offsec/cloud-pentesting/cloud-redteam-operation/domain-fronting-and-redirectors" %}



Domain fronting is a collection of techniques to make use of other people’s domains and infrastructure as redirectors for your controller.

A trivial form of domain fronting is to stand up a node in Amazon’s EC2 and configure it as a redirector for your controller. The FQDN of your EC2 instance is an amazonaws.com subdomain.

AWSSTATIC > high reputation -> point to cloudfront.net which serve our malicious webserver content on polo.malicious.com

* Example

`wget -U demo -q -O - http://a0.awsstatic.com/foo.txt --header "Host: d16b91n8fagr3u.cloudfront.net"`

**Resource:**

{% embed url="https://blog.cobaltstrike.com/2017/02/06/high-reputation-redirectors-and-domain-fronting/" %}





