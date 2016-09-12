# openwrt_ipip6  
A user-modified script for adding IPv4/IPv6-tunnel on OpenWrt "Chaos Calmer".  
The work is mostly based on the already-available script "dslite.sh" included in the package 'ds-lite'.  
As for the usage of this script, copying the script "ipip6.sh" to the paths described below should be sufficient (means you really don't need any additional files besides the interface definition written in "/etc/config/network").  
These paths on my Buffalo WZR-HP-G300NH are:  
"/lib/netifd/proto/"  
"/overlay/upper/lib/netifd/proto/"  
(Maybe you just need one of them, but I haven't figured that out...)  
  
##You are free to download and use this script as long as the following situations sound okay with you;  
  
###Situation-1.)  
This script was intentionally written to satisfy my personal needs for standard IPv4/IPv6-tunnel on OpenWrt. It is comfirmed to be in a working state as of Sept. 12 2016, but beware that no garantee is expressed here. As often done so in many opensource communites, you are still free to fork it (but with full respect to the authours of work I based this script on), modify it, open issues, or submit pull-requests - yet here, expect no technical supports with formality (either from me, or OpenWrt dev team).  
"I'll try my best to be there to help, but that's not my job."  
  
###Situation-2.)  
Writing/modifying scripts like this is often very easy (in fact, far easier than C to me), so if you feel like asking me for technical supports, I strongly urge you to learn how to read it at least - I "urge" you, because they are so much fun to play with. They are called shell-scripts.  
  
###Situation-3.)  
I don't intend to declare this with clarity, but I strongly believe that rights of this script "should" belong to OpenWrt dev team - obviously for the parts I have quoted (more like "copied") from the original work "dslite.sh", but also for the parts I have modified/added. I strongly expect that those downloading this script understand this attitude. I'm making this script available here under my own repository (but I take no responsibility for malfunction like I said, okay?), simply because the issue I have opened regarding the treatment of IPv4/IPv6-tunnel did not gather any notable attention. The package "ds-lite" I think is great in the way that it can take hostname as an arguement for the option "peeraddr" (and I depend on that feature), but I also believe that the script "dslite.sh" included in "ds-lite" is not conventional since you cannot specify IPv4 addresses (both local and remote) of the interface. 
  
I love OpenWrt, and for the love I have for it, I really don't want any troubles with potential users of the script and/or OpenWrt dev team - that's all I am saying. I guess, and I hope this is fair enough.
