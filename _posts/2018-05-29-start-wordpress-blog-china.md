---
type: post
title: Start a Wordpress Blog in China
seotitle: How to Start a WordPress Blog in China (Updated 2018)
author: Mighil
description: Here's an ultimate step-by-step guide on how to start a WordPress blog in China. This beginner-friendly tutorial will be straight to the point.
headerimage: start-wordpress-blog-china.png
updated: 2018-05-28T16:52:36+00:00
sitemap:
  lastmod: 2018-10-15T11:59:57+00:00
tags: website china-blogger
url: /start-wordpress-blog-china/
---
<img align="center" src="/images/start-wordpress-blog-china.png" alt="How to Start a WordPress Blog in China" width="auto" />


A lot of expats in China prefer to share their adventure in China with their friends back at home. Legends say starting a <a href="https://www.quora.com/Is-WordPress-blocked-in-China/answer/Mighil">WordPress blog in China can be painstaking</a>. That's bullshit. All you need is a VPN service to get started.



<strong>Major Update: Sep 14, 2018</strong>



CloudWays Singapore servers are performing well in mainland China. Here's <a href="https://www.chengdudigital.com/">an example site</a> based on CloudWays that caters mainland audience. I highly recommend you to check their services to speed up the process. They offer one-click WordPress install as well. <a href="https://mighil.com/start-wordpress-blog-china/#a-vpn">Sign-up with a VPN service</a>, <a href="https://mighil.com/start-wordpress-blog-china/#b-domain-name">buy a domain</a> and visit CloudWays.

<p style="text-align: center;"><a class="button-dark" href="https://mighil.com/go/cloudways">Get Started for FREE (You Can Run Multiple WordPress Also)</a></p>

**Table of Contents**

* [Why WordPress](#why-wordpress)
* [Custom Solution](#custom-solution)
* Prerequisites:
* a. VPN
* b. Domain name
* c. A Virtual Private Server (VPS) to host your website.
* d. Putty or Terminal and WinSCP or Cyberduck
* e. Others
* A. Buy A Domain
* B. Add Site to Cloudflare
* C. Create A DigitalOcean Droplet
* Note:
* D. Install VestaCP On CentOS
* Step 1: Login to your server as root
* Step2:  Install Vesta CP
* E. Configure DNS
* F. Add New Website on VestaCP
* Step 1: Visit the VestaCP login URL.
* Step 2: Add a website
* Step 3: Create a Database for WordPress
* G. Download And Install WordPress

<h2 id="#why-wordpress">Why WordPress</h2>

Dedicated hosting can be pricey since they come with one-click tools. A lot of blogging platforms doesn't work well in China as well.

So, it's wise to host your own WordPress blog. I've prepared this ultimate guide to teach you how to make a self-hosted personal WordPress website in China.


<strong>Note:</strong> This post contains 2 affiliate links and a referral link. Which means I will earn a small commission when you purchase using my links. No extra cost to you.

<h2 id="#custom-solution">Custom Solution</h2>

Sit back and relax, I can personally help you start a WordPress blog in China for the price of a coffee.

<h2>Prerequisites:</h2>

<h3>a. VPN</h3>

A VPN is essential. A lot of websites I'm going to mention below doesn't work well in China. Feel free to use my <a href="https://www.linkev.com/?a_aid=mighil">affiliate link</a> in the sidebar to sign-up with Express VPN. Their service is pretty good in China.

<h3>b. Domain name</h3>

A domain name is an identification string that defines a realm of administrative autonomy, authority or control within the Internet. You know the drill; go ahead and buy a domain name that reflects your brand name.



I prefer NameCheap over Gandi.net since it has got a faster interface. Go ahead and use <a href="https://namecheap.pxf.io/c/1155193/386170/5618">my affiliate link</a> (starts from 0.88USD/year) if you prefer to register a domain using namecheap.com.

<h3>c. A Virtual Private Server (VPS) to host your website.</h3>

A Virtual Private Server (VPS) is a virtual machine sold as a service by an Internet hosting service. Many companies including Aliyun in China offer virtual private server hosting or virtual dedicated server hosting as an extension for web hosting services.



There are several challenges to consider when licensing proprietary software in multi-tenant virtual environments. With unmanaged or self-managed hosting, the customer is left to administer their server instance. However, shared/dedicated hosting + cPanel in China can be pricey.



Services like Hostgator comes with one-click options, but you've got to pay the price for the same. So, we'll be self-managing a DigitalOcean droplet (VPS) based on Ubuntu or CentOS.

<h4>Why DigitalOcean?</h4>

Even though, DigitalOcean is not for everybody. As a beginner, it's something I'd recommend. You can learn a lot more about VPS in general when you start from scratch without anyone's help. Feel free to join DigitalOcean using <a href="https://m.do.co/c/fe21fc640198">my referral link</a>.

<h3>d. Putty or Terminal and WinSCP or Cyberduck</h3>

<h4>Putty or Terminal</h4>

You'd need an SSH client to login to your VPS.



PuTTY is an SSH and telnet client, developed originally by Simon Tatham for the Windows platform. Use Terminal if you're using a Mac.

<h4>WinSCP or Cyberduck</h4>

Not everyone is a Linux savvy. As a beginner, you won't be flexible with using Linux commands to move/copy and edit files. Hence you'd need an SFTP/FTP client to view, edit and manage the data on your server.



WinSCP is a free and open-source SFTP, FTP, WebDAV, Amazon S3 and SCP client for Microsoft Windows.



I suggest Cyberduck for Mac users since I use it often. You have other options like FileZilla for Windows and Transmit for Mac. Use any SFTP software you're comfortable with.

<h3>e. Others</h3>

<ol>

 	<li>You'll be using VestaCP (free and open-source control panel) as the default VPS control panel to host the WordPress website on your server.</li>

 	<li>For the managed DNS part and to speed up your website in China, I'd suggest Cloudflare since their interface is sleek. They also provide a free SSL. Having a Cloudflare generated SSL certificate is crucial since Google will be counting HTTPS as a ranking factor. Go ahead, visit cloudflare.com and create an account right away.</li>

</ol>

I hope you've got a basic idea now. Fire up ExpressVPN, let's <strong>start a WordPress blog in China</strong>.

<h2>A. Buy A Domain</h2>

Purchasing a domain on NameCheap is pretty much straight-forward. <a href="https://namecheap.pxf.io/c/1155193/386170/5618">Sign-up</a>, search for a domain name of your choice, add it to the cart and make payment. After the purchase, <a href="https://ap.www.namecheap.com/domains/list">visit this URL</a> and click "manage".



<strong>Note:</strong>

<ul>

 	<li>You can purchase a <strong>.cn</strong> domain and host it outside of China with the help of Chinese friend.</li>

 	<li>You don't need a China ICP license for hosting the .cn domain outside of China.</li>

</ul>

<img class="size-full wp-image-2930 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/buy-manage-namecheap-domain.png" alt="Buy and Manage Domain NameCheap" width="1478" height="600" />



Once you click "manage", you'll see something like this.



<img class="size-full wp-image-2932 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/manage-domain.png" alt="Manage NameCheap domain" width="1464" height="758" />



Keep the browser window idle and proceed to the next step.

<h2>B. Add Site to Cloudflare</h2>

Visit cloudflare.com and log in to your account. Visit this URL or click "+ Add Site" located in the upper right corner.



<img class="size-full wp-image-2933 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/cloudflare-add-site.png" alt="Cloudflare Add Site" width="1910" height="637" />



Now fill in your domain name and click "Add Site."



<img class="size-full wp-image-2935 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/cloudflare-add-domain.jpg" alt="Cloudflare Add Domain" width="901" height="419" />



Click "Next", select the free plan and click "Confirm Plan."



<img class="size-full wp-image-2934 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/cloudflare-free-plan.jpg" alt="Cloudflare Free Plan" width="1198" height="537" />



Now, wait for Cloudflare to finish querying your DNS records.



<img class="size-full wp-image-2936 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/cloudflare-dns-query.png" alt="Cloudflare DNS Query" width="907" height="574" />



Usually, Cloudflare will return your current DNS settings (aka NameCheap default settings). But sometimes it may display an error like "we are unable to find your DNS settings." Just click "Next".



As you can see below, Cloudflare will ask you to change your nameservers.



<img class="size-full wp-image-2937 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/cloudflare-nameservers.jpg" alt="Cloudflare Nameservers" width="1045" height="579" />



Visit the idle window I mentioned at the end of step 1. Select the "Custom DNS" in the NAMESERVERS section and fill the nameservers as suggested by Cloudflare and Click save.



<img class="size-full wp-image-2938 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/cloudflare-custom-dns.jpg" alt="Cloudflare Custom DNS" width="1157" height="563" />



Switch the active window to the Cloudflare setup and click "Continue." Give it a few minutes for the DNS propagation. The Cloudflare status will be "Active" after DNS propagation.

<h2>C. Create A DigitalOcean Droplet</h2>

DigitalOcean calls its cloud servers Droplets; each Droplet you create is a new server for your personal use.



If you are a new user, DigitalOcean will ask you either top up 5$ credit or add a preferred payment method.



I'd top up 5$ via PayPal since it's the wise choice than adding a credit/debit card. Now sign in to your DigitalOcean account and <a href="https://cloud.digitalocean.com/dashboard">visit the dashboard</a>.



Click "Create Droplet" and refer to the screenshot below:



<img class="size-full wp-image-2939 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/create-droplet-digitalocean.png" alt="Create Droplet DigitalOcean" width="1047" height="3020" />



DigitalOcean VPS pricing starts from 5USD per month. Choose an ideal server for your personal website.



<strong>Since we are in China, I'd recommend Singapore location for hosting the WordPress site.  </strong>



<strong>CloudFlare has got data centers in China, and it will make sure your website delivers content without any lag.</strong>



Go ahead and select the 5USD server if you are setting up a personal website aiming less than 10k users per month.

<h3>Note:</h3>

<ol>

 	<li>You can upgrade and optimize droplets whenever you like.</li>

 	<li>I've selected Ubuntu 16.04.4. You can choose CentOS 7.5 x64 as well. Keep in mind that Ubuntu uses apt with DEB packages, while CentOS uses the YUM package manager with RPM packages. In this tutorial, I will be using "yum" often. CentOS is believed to be more stable because it has less frequent updates to their packages.</li>

 	<li>I highly recommend readers to learn more about SSH keys and generate/set-up SSH keys while creating a droplet. SSH keys provide a more secure way of logging into a virtual private server with SSH than using a password alone.</li>

</ol>

Click "create" if everything looks ok for you. DigitalOcean will generate Public IP, one-time root password and send it over to your registered email address.

<h2>D. Install VestaCP On CentOS</h2>

<h3>Step 1: Login to your server as root</h3>

Use the credentials DigitalOcean sent you over email to log in.



Open up Putty on Windows. Things are pretty much intuitive on Windows. If you find it confusing, <a href="https://mediatemple.net/community/products/dv/204404604/using-ssh-in-putty-">read this article</a>.



In case you are using a Mac, open Terminal, type the following and hit enter:

<pre>$ ssh root@67.218.xxx.xx</pre>

<strong>Replace 67.218.xxx.xx with your server's IP address. </strong>



After logging in for the first time, DigitalOcean's Linux distro will force you to change the password. Just do it.

<h3>Step2:  Install Vesta CP</h3>

Download installation script

<pre>$ curl -O http://vestacp.com/pub/vst-install.sh</pre>

Run it to start the installation

<pre>$ bash vst-install.sh</pre>

Ubuntu may ask you to force the installation sometimes. Run this command to do it:

<pre>$ bash vst-install.sh -f</pre>

It will ask you type in the host name and email address. It's wise to not use your <strong>domainname.tld</strong> as the hostname.



Use something like <strong>cp.domainname.tld. </strong>



VestaCP roughly needs 5 to 10 minutes to finish the installation.  It will display the login URL and admin credentials upon completing the installation.

<h2>E. Configure DNS</h2>

Visit the DNS section of your website in Cloudflare.com.



Set CNAME and A records as follows.

<ul>

 	<li>A Record - Name: @, ipv4 address: 67.218.xxx.xx</li>

 	<li>A Record - Name: cp, ipv4 address: 67.218.xxx.xx</li>

 	<li>CNAME record - Name: www, Domain Name: @</li>

</ul>

<strong>Don't forget to replace 67.218.150.74 with your server's IP.</strong>



Make sure it looks like this after editing.



<img class="size-full wp-image-2956 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/dns-records.jpg" alt="Cloudflare DNS" width="989" height="770" />

<h2>F. Add New Website on VestaCP</h2>

<h3>Step 1: Visit the VestaCP login URL.</h3>

It may look like <strong>https://67.218.xxx.xx:8083</strong>



Log in using the credentials you saved before. Change the admin password after logging in.



Feel free to tweak other settings according to your preference.

<h3>Step 2: Add a website</h3>

Visit the WEB section in the VestaCP and click the "<strong>ADD WEB DOMAIN</strong>" button.



<img class="size-full wp-image-2941 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/vestacp-new-domain.png" alt="VestaCP Add New Domain" width="1046" height="932" />



Fill in the domainname.tld (eg: mynewsite.com) and select the default IP address. Click the <strong>ADVANCED OPTIONS</strong> and edit the Alias to www.domainname.tld. Click "Add" when you're ready.



<img class="size-full wp-image-2942 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/new-domain-vestacp.jpg" alt="VestaCP New Domain" width="956" height="687" />



Wait for few seconds and visit domainname.tld. You'd see a dummy home page generated by VestaCP.

<h3>Step 3: Create a Database for WordPress</h3>

VestaCP has installed default software stacks required for WordPress.



You have to create MySQL database right now so we can use the same during WordPress installation.



To do this, visit the DB section of your VestaCP. Click "Add DB and fill in the details.



<img class="size-full wp-image-2943 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/vestacp-db.jpg" alt="VestaCP Database" width="995" height="866" />



<strong>Note:</strong> Prefix admin_ will be automatically added to database name and database user. It's a VestaCP setting by default.



Click "Add" when you're ready. Save the database details somewhere safe.

<h2>G. Download And Install WordPress</h2>

Oh boy! we're almost there. Let's install WordPress already!



Login to your VPS using Putty/Terminal as root user. Use cd to navigate to the domainname.tld folder located inside the home folder.

<pre>$ cd /home/admin/web/domainname.tld/public_html/</pre>

Go ahead and download WordPress to the public_html folder using the following command:

<pre>$ wget http://wordpress.org/latest.zip</pre>

Now unzip the wordpress.zip folder by:

<pre>$ unzip latest.zip</pre>

Wait patiently and let it finish the thing.



Move it from wordpress folder to the public_html folder afterwards:

<pre>$ cd wordpress

$ shopt -s dotglob; mv -- * ..</pre>

Now go back to the public_folder.

<pre>$ cd /home/admin/web/domainname.tld/public_html/</pre>

Delete the default index.html file and the WordPress folder generated while unzipping.

<pre>$ rm index.html

$ rmdir wordpress</pre>

Now move the wp-config-sample.php to wp-config.php using the following command:

<pre>$ mv wp-config-sample.php wp-config.php</pre>

Now you have to edit the wp-config.php file. You may use WinSCP/Cyberduck to do the same.



Connect to your server using the root credentials. Open the wp-config.php file located in /home/admin/web/domainname.tld/public_html/



<img class="size-full wp-image-2944 aligncenter" src="https://mighil.com/wp-content/uploads/2018/05/wp-config.jpg" alt="how to edit wp-config.php" width="640" height="502" />



Replace database_name_here with the database name you've generated on VestaCP. Fill in the username, password as well and click save.



Open Putty/Terminal again and log in to your VPS as the root user.



Run this command to set chown rules for VestaCP admin user:

<pre>$ chown -R admin:admin /home/admin/web/domainname.tld/public_html</pre>

It will come handy when you're about to install a new theme/plugin on Wordpress.



Now visit your website and finish the WordPress installation.



<a href="https://jonnyjordan.com/blog/how-to-setup-cloudflare-flexible-ssl-for-wordpress/">Read this guide</a> to setup CloudFlare flexible SSL for your WordPress website.



<strong>That's it, happy WordPress powered blogging in China!</strong>



<a href="https://mighil.com/contact"><img class="aligncenter wp-image-2950 size-full" src="https://mighil.com/wp-content/uploads/2018/05/wordpress-setup-assistant.png" alt="1&amp;1 WordPress Assistant" width="1200" height="211" /></a>



If you have set-up a new blog about your life in China feel free to share the link via email. I'll add you to the "great success" list.



Direct all technical questions to <strong>WeChat: </strong>mighil<strong>.</strong>
