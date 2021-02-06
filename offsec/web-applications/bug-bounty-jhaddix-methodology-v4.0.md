# Bug Bounty jhaddix Methodology v4.0

## Bug Bounty jhaddix Methodology v4.0

![](../../.gitbook/assets/62e7714777394040a5d3bf6c4728484f.png)

![](../../.gitbook/assets/8e5f2bb3cbd8407ea378010f76d0242e.png)

![](../../.gitbook/assets/c6a7dbc0a4f8463faba79435658d57ce.png)

### Find Seeds/Root domain

[https://crunchbase.com](https://crunchbase.com)

organisation info

### Search for ASP

[https://bgp.he.net](https://bgp.he.net)

### enumeration

* metabigor

`echo 'tesla' | metabigor net --org -v`

* asnlookup

`python asnlookup -o tesla`

* amass

`amass intel -asn 46498`

* reverse whois

[https://whoxy.com](https://whoxy.com)

![](../../.gitbook/assets/1040e9b9e13c4782a8a20847e5bc592b.png)

* vysecurity domlink `python domlink -d vip.com -o vip.out.txt`
* builtwith

[https://builtwith.com](https://builtwith.com)

* Google-Fu

"copyright"

* Shodan

## finding subdomains

![](../../.gitbook/assets/ee463b9e1d10435ab4c0a7f665b21132.png)

### Linked Discovery

![](../../.gitbook/assets/354fde737054468e88f9c84c9ba015c0.png)

### Burp Advanced scope

![](../../.gitbook/assets/329a436905494c08bf2002a68b04ccdc.png)

#### Spider

ctrl + A -&gt; spider and start over again :\)

#### export

Engagement tools -&gt; analyze target -&gt; html

![](../../.gitbook/assets/587d003703634f6cb3b2ec8ba7259f5d.png)

#### Without burp :

hakrawler or goSpider

![](../../.gitbook/assets/7e5e65a34d8543ee88ed31d1b511fded.png)

### Subdomainizer

Can find cool stuff , then search in burp history ...

![](../../.gitbook/assets/9bcc1b35eb394044bc50977edbf1fc42.png)

## Subdomain Scraping

![](../../.gitbook/assets/19fb4f21b3744bc1b09d084b8a7c7703.png)

* Amass
* Subfinder\(v2\) =&gt; projectdiscovery.io
* github-subdomains.py

gwendal Le Coguic

![](../../.gitbook/assets/d538171259714c2ea57d3b4408110803.png)

* Shodan parser

shosubgo

* Cloud range

![](../../.gitbook/assets/58de742142914a538f424fdca20a5d25.png)

## Subdomain brutefoce

* amass using -rf
* shuffleDNS \(projectdiscovery\)
* wordlist tech from tomnomnom
* commonspeak2 \(github assetnote\)

![](../../.gitbook/assets/6ccd4af49ac441779b0ab215d36e59ab.png)

## WAF bypass

![](../../.gitbook/assets/3bcfa709901b474fac174275f12739ff.png)

## Port Analysis

### Masscan

`masscan -p1-65535 -iL $ipFile --max-rate 1800 -oG $outputfile.log`

### dnsmasscan

![](../../.gitbook/assets/a5dca4e06a414cdf83ceb9a6d1324225.png)

## Service Scanning

### brutespray

![](../../.gitbook/assets/7a2e34c854fb4ff49a572af82bd67f2f.png)

## Github dorking

![](../../.gitbook/assets/6cce085664ca41ae85b977619619f1ce.png)

## Screenshot

Aquatone - Eyewitness

## Subdomain Takeover

![](../../.gitbook/assets/2afbd83d75e34fc3a22b564940f19198.png)

* Subover
* nuclei \(projectdiscovery,\)

![](../../.gitbook/assets/0bf21fb650a8422587ba23d233a5900f.png)

## Automation

* interlace 

![](../../.gitbook/assets/6440d3aacf3e42459c35dabc4e414932.png)

