---
seotitle: How to Setup A Shadowsocks Server on DigitalOcean VPS - Mighil
title: Setup Shadowsocks Server on DigitalOcean VPS
description: Learn how to install Shadowsocks server on DigitalOcean Ubuntu droplet easily. Write to mighil[at]mighil.com or connect with me on WeChat if you want me set it up for you for a small fee.
author: Mighil
type: post
date: 2016-12-08T05:42:38+00:00
updated: 2018-10-16T07:45:22+00:00
headerimage: shadowsocks-china-digitalocean.png
sitemap:
  lastmod: 2018-10-16T07:45:22+00:00
url: /how-to-setup-shadowsocks-server-on-digitalocean-vps/
featured_image: /wp-content/uploads/2018/05/shadowsocks-china-digitalocean.png
tags:
  - shadowsocks
---
<figure style="width: auto">
<img src="https://mighil.com/wp-content/uploads/2018/05/shadowsocks-china-digitalocean.png" alt="How to Setup Shadowsocks Server on DigitalOcean VPS">
</figure> 

Shadowsocks is an open source SOCKS5 proxy which, according to their official site, is designed to protect your internet traffic. As an expat in China, I have tried few VPN services. The major downside of well-known providers is that their VPNs create one connection for all traffic (which is easier for China’s GFW to detect/block/slow down).

Recently, I tested Shadowsocks on an Ubuntu server based in Singapore and I must say I’m quite happy with SOCKS5 rather than the paid services. I know there are a bunch of tutorials out there on how to configure Shadowsocks. But, I’d like to be more precise providing the best tips and workarounds.

In this tutorial, you’ll learn how to install Shadowsocks and related packages on an Ubuntu server and bypass the Great Firewall of China.

## Prerequisites

  1. A DigitalOcean droplet (preferably an Ubuntu or CentOS x64 server) / Cost: starts from $5 per month. Feel free to sign-up with [my referral link][1] if you’re interested.
  2. Notepad++/Sublime Text Editor if you don’t prefer UNIX vi editor.
  3. SFTP/FTP client like WinSCP if you prefer a GUI.

## How To Create A New Droplet In DigitalOcean

Note: I highly recommend new users to generate/set-up SSH keys while creating a droplet as they provide a more secure way of logging into a virtual private server with SSH than using a password alone.

<img class="aligncenter size-full" src="https://media.licdn.com/dms/image/C5612AQHkxZsoNtYrtQ/article-inline_image-shrink_1500_2232/0?e=2125872000&v=beta&t=0XF2H4Uaws6fkMydKUD47MQJ_3BEp9hJEaB0JX-Gsh8" width="919" height="1500" />

## How To Install Shadowsocks on Ubuntu 16.04

Let’s fire up putty or any other SSH client and log in to your server as root user.

<img class="aligncenter size-full" src="https://media.licdn.com/dms/image/C5612AQGwmtjq0clH1Q/article-inline_image-shrink_1500_2232/0?e=2125872000&v=beta&t=xuKk3dOpj6BBeaKDbxLFBixYUwPNNtRDaSA61hJF9iM" width="660" height="417" />

Once you have logged in to the server, run the following command to update the packages:

<pre>$ apt-get update</pre>

Now, run the following commands to install Python then Shadowsocks:

<pre>$ apt-get install python-pip
$ pip install shadowsocks</pre>

Now install M2Crypto, which is the most complete Python wrapper for OpenSSL featuring RSA, DSA, DH, EC, HMACs, message digests, symmetric ciphers (including AES). Run the following commands to install M2Crypto:

<pre>$ apt-get install python-m2crypto
$ apt-get install build-essential</pre>

Since salsa20 and chacha20 are fast stream cyphers. Optimized salsa20/chacha20 implementation on x86_64 is even 2x faster than rc4 (but slightly slower on ARM). You must install libsodium to use them:

<pre>$ wget https://github.com/jedisct1/libsodium/releases/download/1.0.10/libsodium-1.0.10.tar.gz
$ tar xf libsodium-1.0.10.tar.gz && cd libsodium-1.0.10
$ ./configure && make && make install
$ ldconfig</pre>

After finishing up the steps above, we must create a .json file (config file) for Shadowsocks. In order to do this, fire up Vi editor or open your text editor and create a new file. Add these data to the file:

<pre>{
"server":"your_droplet's_IP_address",
"server_port":8000,
"local_port":1080,
"password":"your_password",
"timeout":600,
"method":"aes-256-cfb"
}</pre>

You can choose any encryption method from [here][2].

Save the file as shadowsocks**.json** and copy it to the **/etc** folder.

Now start your Shadowsocks server. Run the following command to do so:

<pre>$ ssserver -c /etc/shadowsocks.json -d start</pre>

You can check the Shadowsocks log file, which is located in **/var/log/shadowsocks.log** to make sure everything is okay.

Now that you are almost done, we need to make sure Shadowsocks server will be started automatically during system reboots. Edit the file named /etc/rc.local to do so.

Open up **/etc/rc.local** and add the following content before the exit 0 line.

<pre>/usr/bin/python /usr/local/bin/ssserver -c /etc/shadowsocks.json -d start</pre>

Now you’re ready to roll.

Note: In the future, use this command: “ssserver -c /etc/shadowsocks.json -d stop” to stop the Shadowsocks server. and “ssserver -c /etc/shadowsocks.json -d restart” to restart.

## Server Optimization

There are a number of ways to optimize your server, here are the best ones.

### To increase the maximum number of file descriptors:

Edit the limits.conf file located in **/etc/security/limits.conf** and add the following two lines:

<pre>* soft nofile 51200
* hard nofile 51200</pre>

Now, temporarily stop the Shadowsocks server to set the ulimit.

Run:

<pre>$ ssserver -c /etc/shadowsocks.json -d stop</pre>

Now set the ulimit:

<pre>$ ulimit -n 51200</pre>

## To optimize the kernels:

We can optimize the kernel parameters by editing the **/etc/sysctl.conf** file. Open up the file and add the following lines to the end of the document:

<pre>fs.file-max = 51200
net.core.rmem_max = 67108864
net.core.wmem_max = 67108864
net.core.netdev_max_backlog = 250000
net.core.somaxconn = 4096
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200
net.ipv4.ip_local_port_range = 10000 65000
net.ipv4.tcp_max_syn_backlog = 8192
net.ipv4.tcp_max_tw_buckets = 5000
net.ipv4.tcp_fastopen = 3
net.ipv4.tcp_mem = 25600 51200 102400
net.ipv4.tcp_rmem = 4096 87380 67108864
net.ipv4.tcp_wmem = 4096 65536 67108864
net.ipv4.tcp_mtu_probing = 1
net.ipv4.tcp_congestion_control = cubic</pre>

Save it and run this command:

<pre>$ sysctl -p</pre>

Now that you finished optimizing, start the server!

<pre>$ ssserver -c /etc/shadowsocks.json -d start</pre>

## Shadowsocks Clients:

Check out the [clients][3] for different platforms listed on Shadowsock’s official website.

 [1]: https://m.do.co/c/fe21fc640198
 [2]: http://www.shadowsocks.org/en/spec/Stream-Ciphers.html
 [3]: http://www.shadowsocks.org/en/download/clients.html
