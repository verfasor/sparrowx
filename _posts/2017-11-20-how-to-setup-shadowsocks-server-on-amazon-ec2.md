---
seotitle: How To Setup A Shadowsocks Server On Amazon EC2 - Mighil
title: How To Setup A Shadowsocks Server On Amazon EC2 
description: Step by step instructions to set up your own speed-optimized Shadowsocks server on Amazon EC2. Write to webmaster[at]mighil.com or connect with me on WeChat if you want me set it up for you for a small fee.
author: Mighil
type: post
date: 2016-12-08T05:42:38+00:00
url: /how-to-setup-shadowsocks-server-on-amazon-ec2/
tags:
  - shadowsocksr
---

## Setup A ShadowsocksR Server On Amazon EC2

<figure style="width: auto">
<img src="https://mighil.com/wp-content/uploads/2018/05/shadowsocks-amazon-ec2.png" alt="How To Setup A Shadowsocks Server On Amazon EC2">
</figure> 


Learn how to install ShadowsocksR (not Shadowsocks) server on Amazon EC2 Ubuntu instance (Free Tier) easily. Unlike the <a href="https://mighil.com/how-to-setup-shadowsocks-server-on-digitalocean-vps/">DigitalOcean guide</a> I posted before, this one involves fewer commands and scripts.. hell yeah!
<h2>Why ShadowsocksR?</h2>
ShadowsocksR is a fork of the original Shadowsocks project, claimed to be superior in terms of security and stability.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*8tKlppUSvL32AkM03E4V4w.gif" />

<strong>Warning:</strong> Although this guide is intended to be 100% n00b friendly, there are chances you may face minor issues or errors during setup. Be prepared. Just write to mighil[at]mighil.com or connect with me on WeChat: mighil if you want me set it up for you for a small fee.
<h3>Prerequisites:</h3>
<ol>
 	<li>Access to AWS console. (Requires one time credit/debit card verification)</li>
 	<li>Read more about EC2 Free Tier.</li>
 	<li>SSH client.</li>
 	<li>Patience.</li>
</ol>
<h3>Step 1. Sign in to the AWS Console &amp; Create an EC2 Instance</h3>
AWS may take you to the US region by default. It’s up to you choose the location.
<h4>1.1 Select EC2 in the Compute Section</h4>
Select Asian region (Tokyo or Singapore recommended) if you’re from China.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*g4wx6W5D12vucwg_tK_2fQ.png" width="920" height="415" />
<h4>1.2 Click Launch Instance</h4>
Go on and read their <a href="https://aws.amazon.com/ec2/getting-started/">Getting Started</a> Guide if you’ve got enough time.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*MRv87GOn_dhTUgvwOs0hWw.png" />
<h4>1.3 Select The Ubuntu Server 16.04 LTS</h4>
Ubuntu Server 16.04 LTS is Free Tier Eligible and that’s what we’re gonna use for this guide as well. Click Select and proceed to the next step.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*JF4AscuxDebZgaQueQk2Xg.png" width="860" height="216" />
<h4>1.4 Choose the Instance Type</h4>
Look for the t2.micro which is Free Tier eligible. Select it and Click Review and Launch.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*XaIRsoLqtQXXiz36LRL7Tw.png" width="868" height="435" />
<h4>1.5 Configure Security Group</h4>
Open the TCP ports you’re gonna use for ShadowsocksR. I’ve set Port Range from 8000–8083 for this guide. You can limit the source according to your preference. Click Review and Launch when you’re ready.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*wXfkhVlzE-RcR7DQXz27cg.png" width="915" height="446" />
<h4>1.6 Create a New Key Pair</h4>
Create, download and save keypairname.pem file in a safe place.

<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*w94nZ6_NkHqd1SmddvbKSw.png" width="955" height="492" />

Congrats on the 60% progress…n00bs, before jumping to the next big step, learn how to use PEM key on Mac. Windows users, you have to convert PEM file to PPK. Please read it here and come back to this article.
<h4>1.6.1 Copy The AWS Generated PEM File to a Safe Location</h4>
Here’s how to copy keypairname.pem to /Users/usrname/.ssh/ (hidden directory)
<ol>
 	<li>Copy the keypairname.pem file.</li>
 	<li>Open Finder, use the shortcut “Shift + Command + G” and type in /Users/usrname/.ssh/</li>
 	<li>Paste the keypairname.pem file.</li>
</ol>
<h4>1.6.2 chmod 400 the PEM file</h4>
We have to set the right permissions for PEM file. Use the chmod command to make sure that your private key file isn’t publicly viewable. For example, if the name of your private key file is keypairname.pem, use the following command:
<pre>$ chmod 400 /Users/username/.ssh/keypairname.pem</pre>
Alright, it’s about time fellas! let's dive into the Terminal/Putty.
<h4>1.6.3 Uncheck this Sucker in Terminal Preferences (Recommended)</h4>
<img class="aligncenter" src="https://cdn-images-1.medium.com/max/800/1*Ht4HLNmHRzJy6iam7I9jgA.png" />
Not necessary but since there are chances some users may get locale errors, it’s a best practice to uncheck this from Terminal Preferences. Check this thread in case you face locale issue.
<h3>Step 2. Connecting to The EC2 Instance</h3>
Let’s connect to your instance from Putty or Terminal:
<h4>2.1.1 Mac:</h4>
<pre>$ ssh -i /Users/username/.ssh/keypairname.pem ubuntu@public.IP</pre>
<h4>How to find your public IP</h4>
Check it from corresponding AWS EC2 webpage or run this command:
<pre>$ wget -qO- -t1 -T2 ipinfo.io/ip</pre>
<h4>2.1.2 Windows:</h4>
Load your PPK and connect to the server as ubuntu user
<h3>Step 3. Switch User</h3>
Once you’re inside the EC2 instance. Switch to root user:
<pre>$ sudo su</pre>
<h3>Step 4. Run The ShadowsocksR Auto-Installer</h3>
Script by  <a href="https://shadowsocks.be/9.html">@teddysun</a>
<pre>$ <span class="hljs-attribute">wget</span> --<span class="hljs-literal">no</span>-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh

$ chmod +x shadowsocks-all.sh

$ ./shadowsocks-all.sh 2&gt;&amp;1 | tee shadowsocks-all.log</pre>
This installer is intuitive and will guide you setup ShadowsocksR on your instance.

Note: It contains installers for other Shadowsocks packages as well.
<h3>4.2 Important:</h3>
The installer will generate and display the final config. It displays Private IP (<strong>not public IP</strong>). So make sure you use Public IP within client apps. As I mentioned EARLIER, <strong>you can find your public IP within the corresponding AWS EC2 instance page </strong>or run this command to display the public IP:
<pre>$ wget -qO- -t1 -T2 ipinfo.io/ip</pre>
<h3>4.3 Commands to start | stop | restart | check status</h3>
<strong>Shadowsocks-Python</strong>：
<pre>$ /etc/init.d/shadowsocks-python start | stop | restart | status</pre>
<strong>ShadowsocksR：</strong>
<pre>$ /etc/init.d/shadowsocks-r start | stop | restart | status</pre>
<strong>Shadowsocks-Go：</strong>
<pre>$ /etc/init.d/shadowsocks-go start | stop | restart | status</pre>
<strong>Shadowsocks-libev：</strong>
<pre>$ /etc/init.d/shadowsocks-libev start | stop | restart | status</pre>
That’s it, congrats on the 100% progress. Write to webmaster[at]mighil.com or connect with me on WeChat if you want me set it up for you for a small fee.