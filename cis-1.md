# Small Business Security - Practical and Free(ish) - Part 1 

## Who, What and Why 

My name is Cory Keller, and I am a Jr. Offensive Security Specialist at Cyber Defense Labs and hold several certifications in the cyber security industry. Who I am aiming this series of blog posts at is the IT rep for small business who are on a limited budget and still need to protect their organization. Whether this IT rep is a security minded person or not. What I want to give you is examples of methods that can bolster a security program or build it from scratch. I will use the Center for Internet Security control list as our guide through this process. These controls are based upon data and wisdom collected throughout the cyber security industry. It will get technical along with the guidance pieces that come about.  
 

Small organizations may have different security requirements. It is ultimately on you to know your organizations governance. Following these controls will get you on the path to compliance with your governance and then some. Compliance, however, will not equate to being secure.  


The tools I am going to recommended will be tested by myself at some point or will be researched and tested for the purpose of the blog. More importantly, budget in mind I will be keeping the tools to the open-source realm. This is not a shot at any commercial piece of hardware or software. However, with open source comes a lot of technical in the weed's explanations, I'm excited for it. I will break them down into easy-to-follow spoon fed steps as well. 

## Center for Internet Security Controls. 
 
The Center for Internet Security (CIS) publishes a list of controls that can be downloaded to apply as necessary to your organization. According to CIS "The controls are a set of prioritized set of actions that collectively form a defense-in-depth set of best practices that mitigate the most common attacks against systems and networks"(CIS,2021). These steps were created and prioritized based off actual attacks from other organizations and the collective wisdom of the contributors.  

The CIS controls are based implementation groups. CIS defines Implementation group 1 (IG1) as "An IG1 organization is small to medium-sized with limited IT and cybersecurity expertise to dedicate toward protecting IT assets and personnel." (CIS,2021). However, we do not need to focus on that exactly. I will focus CIS controls based on the needs of IG1 as I wanted these businesses to benefit from practical security measures, so they do not get picked off by some keyboard jockey looking for low hanging fruit.  

Also, I am aiming these solutions to be scalable. If in a few years you find yourself working for a different organization in IG2/3 or the organization grows into IG2/3 you have something to work with. If you follow along with the entirety of the series keep in mind that these controls tie into each other and blend together.  

Keeping that in mind the first step might not be the sexiest technically...but it is arguably the most important and as long as we keep the list a living document it makes it easy to maintain for the lifecycle of hardware and software alike. These steps will also reward you in making controls like application locking/whitelisting easier to perform alongside MAC address whitelisting.  

## FINALLY, he is done talking and going to show me how to start doing... 

### CIS Control # 1. 

### Inventory and Control of Hardware Assets. 

This is the first and most important step. You need to create a living inventory of your hardware. It is important that you understand what you have. You cannot possibly maintain a secure environment if you do not know what you need to secure. Losing sight on your attack surface leaves you open and vulnerable in areas you may never knew you had, and it will be over before you catch it. Depending on your organization's income flow the fines associated with the governance could be a spear through the heart of the company. 

Maintaining a detailed asset inventory that is living will go long ways into making security effortless in the near future. Addressing network related controls for your organization can be as easy as uploading a document to your router/switches to allow only these identified MAC addresses. "\Once MAC addresses are confirmed, switches should implement 802.1x and Network Access Control (NAC) to only allow  

authorized systems that are properly configured to connect to the network"(CIS,2021). It is more cumbersome to do these steps as an afterthought. Doing them now saves you heartache and time later. Think of it allowing you to be lazy later ;).  

Even better you can create a logical layout of your network with surety as you have the assets you listed and that they are what is authorized to communicate on your network. 

Think of it as... 

![Mouseketoodlie](~/images/mickey.jpeg)

### BUT HOW... 

Well...whatever works for you. I would strongly avoid the old' excel spreadsheet. They become customized to someone else's way of thinking. Whatever you make I recommend the following: 

```markdown 
1. Serial number 
2. MAC Address 
3. Vendor 
4. Device Type (Computer/laptop, mobile devices or IoT, networked cameras and environmental controls, switches/routers, network security (firewall, IDS, IPS, Proxy) 
```

### Automation 

Let us say you are an established organization and have quite a few assets deployed and cannot afford to take them down to open the case and get the information you require. You can implement some automation to discovery of these assets and identification of authorized devices. Various open-source tools like nmap allow you to scan for hosts on your network, it returns information valuable to you. There are software programs that will ingest nmap output to present a visual on the data you are reading, or you can use the greppable output to grep out what you are looking for... 

I know what you're thinking... 

![U2-Still looking](~/images/u2.jpeg) 

This is where tools during and after your inventory help out. Tools like "Snipe-IT" allow for an easy approach to asset management. As a bonus they have a free forever approach.  

```markdown 
https://github.com/snipe/snipe-it/releases/tag/v5.2.0 - This link takes you to their latest release (at the time of this blog). 

https://snipe-it.readme.io/docs - This will take you to their documentation. 
``` 

![Snipe-IT](~/images/snipeit-install.png) 

Even better they have this as a docker container. This will make installation a breeze. 

You can choose to install it locally with a container(easier) or configure a machine to be able to run the software locally. Both of which may take some time, but the documentation is solid and will get you there and running snipe-it.  

Here is what it looks like to see all assets listed out... 
 
![All Assets](~/images/all-assets.png)  

# The left hand talking to the right hand 

## CIS Control #2 

### Inventory and Control of Software Assets 

Inventorying and keeping up with software can be difficult, especially since you may be starting in an environment where there is little to no inventory existing. Now it is on you to not kick the can and do something about it. Fortunately, we already installed a piece of software that will do the heavy record keeping for us.  

The criticality of this information's importance is exactly the same as the physical hardware. Scenario: You're driving to work and listening to a technology/security news related podcast, and they mention a piece of software that sounds familiar with the version number. You're concerned, they rated this a critical but there is a patch for it. You get into work and check your asset management device and see you have that software and the vulnerable version. You act fast and patch it. You stopped your organization from falling victim.

Now here is my real-world scenario. You listen to that security new podcast. You find out a certain "olarSae indsWae rionOae" software has a terrible vulnerability. You are not sure you have it; you are not sure of what version if you do and cannot find what device you need to patch if you do have it... because you do not have an accurate living inventory. The inventory you thought that was created by a predecessor was not up to date. It was an excel spreadsheet, no one has been updating it...in years. So, no you need to mitigate the risk, you're spending half your day trying to find out the simple answer of whether you do or do not have a risk. Turns out later you have that software, but do not have that version that is vulnerable...You lucked out. Not so many organizations were as lucky.  

Defining a process that works for you is just that. It is on you, and YOU decide what is needed for you. But if you use a tool like "Snipe-IT" to manage this information then you are going to need at minimum/applicable the following: 

```markdown
1. License/Vendor.
2. Product Key. 
3. Expiration date. 
4. Email Information.
5. Point of Contact. 
6. Manufacturer.
7. Version number.
8. Count/Total. 
``` 

![Software](~/images/software-assets.png) 

This is coming from Snipe-IT but those are solid pieces of information to use no matter what product as well you find yourself downloading. I have used Snipe-IT in a limited capacity for the purposes of this blog. There is a demo here... 

```markdown 

https://snipeitapp.com/demo 

``` 

This will at least allow you to determine if it can work for you (hint: it can) and get a feel for how to use that software as well. 

# CIS #1 and #2 Summary 

These controls go hand in hand and should not be skipped and they will empower you to enable powerful OS and network controls as we go along like Network Access Control and AppLocker/Windows Firewall (my personal favorite and our special guest appearance). The risks associated to a IG1 organization may be lower than that of an IG3 org, but the opposing players may not be concerned with your title. It can simply be as easy as you have a misconfigured piece of software on a server you do not know about...oh and it is several security patches behind, with an exploitable vulnerability.  

# References 

https://www.cisecurity.org/controls/ 

https://snipeitapp.com/ 

 
