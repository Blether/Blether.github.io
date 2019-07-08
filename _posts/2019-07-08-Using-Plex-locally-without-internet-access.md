---
layout: post
title: Using Plex locally without internet access
---


Interestingly Plex checks authentication even for clients running locally. 

This is generally transparent and painless, but sometimes one might want to use the Plex server without good access - for example, while travelling. 

Helpfully, the Plex network settings allow for whitelisting of addresses or ranges to connect without authentication. 

This can be done using the usual web interface

[How to Use Plex Media Server Without Internet Access](https://www.howtogeek.com/303282/how-to-use-plex-media-server-without-internet-access/amp/)

Best done beforehand while internet access still available. 

It is possible to use the command line as a fallback: 

[Advanced, Hidden Server Settings | Plex Support](https://support.plex.tv/articles/201105343-advanced-hidden-server-settings/)

>There are a number of advanced, hidden Plex Media Server settings, some of which are not available from the normal interface. Instead, they’re available where your Plex Media Server stores its own settings. The vast majority of users will never need to alter these settings. We recommend exercising caution when considering altering these settings.


Examples:
`defaults write com.plexapp.plexmediaserver LogNumFiles 10`

||
|:-|:-|:-|:-|:-|:-|
|DlnaEnabled	| 1/0	| Disables DLNA server if set to 0	| 0|
|
|allowedNetworks|	string with ip/netmask|ip/netmask|	A list of networks that are allowed to access PMS without authentication. Must be listed with full subnet.	|192.168.1.0/255.255.255.0|10.10.10.0/255.255.255.0|


So the answer could be to try

~~~
defaults write ...

~~~
