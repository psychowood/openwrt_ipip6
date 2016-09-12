#openwrt_v6tunnel : modified script for adding IPv4/IPv6-tunnel on OpenWrt "Chaos Calmer"  
Make sure that you have satisfied prerequisites for the package "dslite" and proceed to copying the script "ipip6.sh" to the appropriate directories.  
These directories on my Buffalo WZR-HP-G300NH are:  
"/lib/netifd/proto/"  
"/overlay/upper/lib/netifd/proto/"  
(Maybe you just need one of them, but I haven't figured that out...)  
The interface definition in "/etc/config/network" should then look something like:  
__config interface 'vpn'__   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option proto 'ipip6'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option peer6addr '2002::dead:beef'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option ipaddr '172.16.0.2'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option peeraddr '172.16.0.1'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option netmask '255.255.255.252'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option tunlink 'wan6'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option mtu '1460'__  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__option defaultroute '1'__  


##You are free to download and use this script as long as the following situations sound okay with you;
###Situation-1.)  
This script is based on "dslite.sh" included in "ds-lite" package, and was intentionally mod-written to satisfy my personal needs for standard IPv4/IPv6-tunnel on OpenWrt. It is confirmed to be in a working state as of Sept. 12 2016, but beware that no guarantee is expressed here. You are still free to fork it (but with full respect to the authors of work I based this script on), modify it, open issues, or submit pull-requests just as often done so in many opensource communities - yet here, expect no technical supports with formality (either from me, or OpenWrt dev team).
The attitude here is "I'll try my best to be there to help, but that's not my job."
###Situation-2.)  
Writing/modifying scripts like this is often very easy (in fact, far easier than C to me), so if you feel like asking me for instructions for beginners, I strongly urge you to learn how to read it at least - I "urge" you, because they are so much fun to play with. They are called shell-scripts.
###Situation-3.)  
I don't intend to declare this with clarity, but I strongly believe that rights of this script "should" belong to OpenWrt dev team - obviously for the parts I have quoted (more like "copied") from the original work "dslite.sh", but also for the parts I have modified/added. I strongly expect that those downloading this script understand this attitude. I'm making this script available here under my own repository (but I take no responsibility for malfunction like I said, okay?), simply because the issue I have opened regarding the treatment of IPv4/IPv6-tunnel did not gather any notable attention. The package "ds-lite" I think is great in the way that it can take hostname as an argument for the option "peeraddr" (and I depend on that feature), but I also believe that the script "dslite.sh" included in "ds-lite" is not conventional since you cannot specify IPv4 addresses (both local and remote) of the interface.  
  
I love OpenWrt, and for the love I have for it, I really don't want any troubles with potential users of the script and/or OpenWrt dev team - that's all I am saying. I guess, and I hope this is fair enough.

