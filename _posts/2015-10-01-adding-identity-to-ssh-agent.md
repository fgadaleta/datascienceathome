---
layout: post
title: Adding identity to ssh-agent
tags: [agent, authentication, identity, nopassword, ssh]
type: post
comments: true
---

One of the most annoying aspects of security is *The password*. 
Even more so every time the Linux console _gently_ asks it a number of times. 
Whenever this occurs once per minute, it gets tiring. 

Those who are dealing with ssh sessions that need authentication, should know about a way to authenticate
once and be safe for the rest of the day (provided no reboot occurs). 

All of this goes under the name of _ssh identity_, namely, if we let ssh know who we
are, it will stop asking for, well, who we are. 
Here is how: 

	`$ ssh-add /home/username/.ssh/id_rsa 
	
	``Enter passphrase for /home/username/.ssh/id_rsa:
	
	Identity added: /home/username/.ssh/id_rsa (/home/username/.ssh/id_rsa) `
	


Happy authentication!

