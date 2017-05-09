---
layout: post
title: Protecting privacy and confidentiality in data and communications
tags: [privacy, confidentiality, encryption]
comments: true
type: post
---

<center>
<img src='/img/img_posts/privacy.jpg' style="max-width:100%;" />
</center>

Talking about security of communication and privacy is never enough, especially when 
political instabilities are driving leaders towards decisions that will affect people on 
a global scale. Those who expect to read about data science and machine learning in this 
post shall postpone their wish to the next post, being the content of this one equally 
important, if not more. 

## Motivation 

As a matter of fact, people are cultivating very bad habits in the way they communicate. 
Many are putting their (digital) life in the hands of those who manage social networks 
claiming they are facilitating the way to communicate. 
Some others are placing their emails in the hands of those who say they are not evil. 
Other people are surfing and searching the Internet with the tools provided by those who say they 
do care of their data and open the doors to security agencies upon request, or, worse keep 
their doors open to intruders and criminals. As a consequence of this superficial behaviour 
with respect to communication, governments and corporations have secured a position that is 
extremely uncomfortable and very very dangerous for all of us. 
It is time to stop this and use powerful technologies that are affordable to many.

## Some common scenarios

The scenario of sharing a document with a co-worker or a friend on Google Drive, together with 
some emails, and of course some calls on Hangout, is without any doubt, extremely rich 
of traces in the hands of...well just one provider. As a matter of fact that same provider can 
and will build a complete profile of their users, of what they write about, how connected 
they are to other peers and much more. If this were not enough, then we should be considering 
the fact that this behaviour will be reiterated massively over a billion other users. 
Every day. Forever.

*"I have nothing to hide"* say those who do not make the effort to secure their communications. 
Sure. Nobody has anything to hide. If that were true it would clearly clash with the fact that
people who make such statements, are the same who are used to lock their doors and text instead 
of shouting when they are in public, not to disclose futile facts like what they are going to 
eat for dinner. 

> Communication that is meant to be private should stay so. Period.

One more subtle scenario is the one of small and large companies that do not pay much attention 
to how their data and communications flow before reaching their destination. 
This information is usually stored for years and can be easily accessed any time by their own 
providers who sometimes are their competitors too. At the time of writing, very few people and 
organizations can claim to have some kind of control over their communications. 
Even those few cases where encryption is used are not always safe. 

Encryption is performed by keys that should stay secret and that are used to lock and unlock  plain text or bits in general. If these secret keys are not in the user's possession, the whole  encryption mechanism does not make sense at all. 

**GDrive** and **Gmail**, just to name a few services that many heavily use 
(I am not excluding myself), 
do not provide these secret keys to their users. This simply means they can read 
all users' documents and emails, any time they want or they are asked to. 
Reading content is essential for companies like Google, and Facebook, in order to personalize 
search and advertisement for their users, which is also the main reason why all these services are
free of charge. 

*"These companies have amazing datawarehouses that are well protected against hackers"* many are 
saying. That's true. That, however, still gives them the ability to access information, or, as happened in the past, to give access to governments whenever they make or impose a request. Moreover, nobody can guarantee that those emails and documents will stay in the same security conditions for the entire lifetime. 

Without getting to the details of the mathematics behind encryption, as mentioned before encryption 
is performed via keys. Whenever corporations claim they are protecting users' data with encryption 
they are not telling the whole story. 

For instance, they usually keep the keys which, as said makes 
the entire encryption process just useless. In order to overcome such an unpleasant situation, many 
secure communication protocols have been created. One of the most prominent so far is the 
[zero knowledge protocol](https://en.wikipedia.org/wiki/Zero-knowledge_proof) which does not 
require any external knowledge to prove that a statement (usually a mathematical statement) is true. 
This means that with a zero-knowledge protocol the provider knows nothing about their users' 
data and they cannot do anything to decrypt data which is physically in their posession, just 
without any key.

Implementing the zero-knowledge protocol and making sure it is correctly deployed is not as easy as 
people think. But the interested user should not worry more, as most of the software we are all 
using in every day life have an equivalent that speak the zero-knowledge language. 

> If these secret keys are not in the user's possession, the whole  encryption mechanism does not make sense at all


Here is a list of "alternatives" to guarantee secure communications whenever required.



## The Search Engine

<center>
<img src='/img/img_posts/duck_google.jpg' />
</center>

As a matter of fact, Google search has been accused to return biased results on queries that are too
personalized. Maybe this is a side effect, maybe not. What matters is that what I search might
 return different results over time not just because the Web is dynamic per se but also because my
interests can change too. In order to do this, Google collects all our personal queries for further
analysis, store them for long periods and never let us know who reads what. Assuming that people 
usually do not lie to their search engine (lieing would not make sense in this context), it turns 
out that Google knows our most intimate secrets, what we think, what we want, what we like, our 
doubts about facts and people. 

[DuckDuckGo](https://duckduckgo.com/) is a more discrete search engine that does not track their users, does not store their queries and just returns whatever the user asked. Bias not included.


## Email and Metadata

<center>
<img src='/img/img_posts/tutanota.jpg' />
</center>

Email analytics is the most subtle out there for two reasons 

1. people write very intimate and confidential messages by private email
 
2. while content can be encrypted, it is much more difficult to guarantee encryption of metadata

Metadata is all data that is required by email servers to 
deliver the message to its destination. Therefore, even in the very rare case email content has 
been encrypted, metadata are still telling the story of who is sending to who. For instance, by 
analyzing the frequency of messages sent to a friend, or relative first, then to an oncologist, or 
psychologist, can disclose a very clear situation: the sender has health or mental issues. 
It is the pattern of communication that is valuable here.

[Tutanota](https://www.tutanota.de) is an opensource secure email service that takes care of encrypting emails without the pain
of storing secret keys. End-to-end encryption is guaranteed also on email attachments and security
and confidentiality are enforced by a unique point of access to [Tutanota](https://www.tutanota.de) servers. This allows users
to communicate using their web browser, mobile device or Android/iPhone app. Tutanota also allows 
creation of email addresses for personal domain to guarantee secure communications especially in 
a business setting. As for storage, 10GB costs as much as a coffee per month.
 
Another valid alternative is ProtonMail which has very similar features, with a slightly different pricing model.


## Cloud Computing and Data Storage

<center>
<img src='/img/img_posts/tresorit.jpg' style="max-width:100%;" />
</center>

As mentioned earlier basically all cloud storage services do not offer any confidentiality feature and when they do they prefer to keep the secret keys that allow them to read whatever has been stored on their servers. Google Drive, DropBox or Box all have the same issues in terms of privacy and encryption. Moreover users' data is not only accessible to them but also to whoever breaks into their servers as already happened at DropBox and Yahoo. 

There are two major secure cloud storage providers worth mentioning: SpiderOak and [Tresorit](https://www.tresorit.com). 

At worldofpiggy.com we have got the chance to try [Tresorit](https://www.tresorit.com) with a premium account for 10 users. Needless to say, we found it really impressive being 100% compatible with Mac, Linux, Windows, and mobile platforms Android and iPhone. Behind a very intuitive interface to share local directories and create so called Tresors, to keep private or share with co-workers and friends, there is an *AES-256* client-side encryption that is fast and secure as it should. 
One very interesting feature is the versioning of shared documents that keeps track of who is changing what, maintaining very strict security policies over time. All documents are synced across devices that can be attached and detached from a very intuitive dashboard. 
Behind all this, a zero-knowledge encryption protocol guarantees that [Tresorit](https://www.tresorit.com) themselves cannot read users' data at all. Not even if they were under control by NSA. Regardless, that would be quite difficult, being Tresorit servers in Europe with data warrants by Swiss privacy law, from which US governments have a lot to learn. 

 


## Surfing the Internet anonimously

<center>
<img src='/img/img_posts/tor.jpg' />
</center>

Writing about [Tor](https://www.torproject.org/) might seem useless as I always assume the average reader knows about it. I will take the risk to repeat myself in this case. [Tor](https://www.torproject.org/) is a free software that plays a role against network surveillance. This is one of the most subtle forms of surveillance as it is not only invisible but also usually not implemented in any of the client applications such as a browser or any messaging app. The concept behind Tor is very simple yet effective. All requests bounce around a distributed network of relays around the world, while encrypting all packets and following different routing paths all the time. This mechanism prevents somebody from intercepting one's communications, websites visited or media downloaded keeping the location of that user always secret.
While [Tor](https://www.torproject.org/) has beed designed to run on any desktop application by setting a proxy that forwards requests to the Tor network rather than the wild Internet, it is now possible to extend this protection to mobile platforms too, in particular Android. Installing Orbot and Orfox (Tor browser) do the trick. All the traffic from Twitter can also be forwarded to the Tor proxy in order to obfuscate the location of the tweets one sends. 


## Password Manager

<center>
<img src='/img/img_posts/keepass.jpg' style="max-width:100%;" />
</center>

Keeping all the passwords that you might be using during your workday is not easy, especially when they all differ. Do they differ, right?

[KeePass](http://keepass.info/) is a free open source password manager, assisting users to securely manage their passwords.
The attempt of Chrome and Firefox browsers to sync passwords and forms across devices literally puts in the hands of the same providers one's passwords hashed from the client. While it is mathematically impossible to reconstruct the password from its hashed version, it is still possible to use those hashes to authenticate (unless two-factor authentication mechanisms are in place). 
I personally do not encourage to store passwords' hashes on the cloud for obvious reasons. I do encourage however to keep them into a password manager like [KeePass](http://keepass.info/), which locks the password database (encrypted with AES or Twofish) with a password. Storing the local database onto an encrypted file system or a shared one with Tresorit would add another level of security (only available to the most paranoid users).



## Mobile Communications

<center>
<img src='/img/img_posts/signal.jpg' style="max-width:100%;" />
</center>

Mobile communications are probably the most at risk just for the fact that people use more their phone than their laptop. WhatsApp has been accused several times for leaving backdoors open/forgot by purpose or mistake. This "mistakes" allow WhastApp employees to read users' messages even when they have been encrypted from the device. As WhatsApp uses a proprietary protocol and app, it is not possible to verify that what they claim is indeed the truth.

Telegram, a more secure mobile messaging application does it better with security and confidentiality as their client code is open source. Their backend however is not, which leads again to a scenario that is not possible to fully verify.

The only mobile messaging app that does it correctly being fully open is [Signal](https://whispersystems.org/blog/signal/). Signal does not need anything more than a phone number (to receive the authentication code) and uses true end-to-end encryption to secure all communications to other [Signal](https://whispersystems.org/blog/signal/) users. 


Of course, this is a suggestion and it really should not be applied to all your communications. There should be a tradeoff between what can be transferred in clear and what you better protect. This tradeoff can only be decided by yourself the only one who knows what is critical and what... is probably not.

As a matter of fact there are very interesting technologies at our disposal and very affordable too. We have the choice of using them.
