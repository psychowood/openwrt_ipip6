Some might ask why this is necessary, and/or if you are curious about the backgrounds for modifying the script, please read on the following.

I am a happy user of OpenWrt in East Japan, whose internet connectivity is widely based on the service called "Flets's Hikari Next" by NTT-East. At home - hence the home I go back to every day - there is a decent setup of networking infrastructure, based around on the YAMAHA RTX3000, Cisco 1812J and AlaxalA AX3630S-24T.

The infrastructure I depend on, hence the "Flets's Hikari Next" is rather interesting, in that the service alone merely provides the access-line to ISP, just like the way we had copper-line to reach us to the dialup endpoint of ISPs in the late 1990s. Although it does provide L3 via IPv6, you are given no connectivity to the WAN/Internet. By default, it's either an L2-mesh with PPPoE support (up to two sessions simutaneously) or an local-WAN or Wide-Area-LAN based on IPv6 - depending on how you feel like calling it. 

Getting access to the web on this service is possible typically by either one of the following "commercial" options;
a.)IPv4 via PPPoE (you have choices of ISPs there, ranging from 500JPY/mo to 100,000JPY/mo depending on what you ask for)
b.)DS-Lite based on IPv6 (requires contract with an ISP)

From the telecom perspective, the primary use of such system (I imagine) is to replace the copper-line based PSTN (both analog and ISDN) by VoIP and imaginably, the monthly fee of its "Lite" service is now as reasonable as those of copper-line based PSTN services.

However, it was not my main focus this time.

Interesting points of this "Lite" service are;
a.)They are cheaper than the regular service, priced around $30/mo (around JPY3,000/mo).
***For comparison, the regular service is priced around $50/mo (around JPY5,000/mo) with unlimited download/upload.
b.)For traffic in excess of 500MBytes/mo involving PPPoE, you will be charged for on the pay-as-you-go basis (but is not "unlimited", so no worries there).
c-1.)Traffic via IPv6 with no involvement of PPPoE counts only 40MBytes/mo towards the monthly usage.
c-2.)Subscribers are able to establish connections with other subscribers of both "Lite" and regular services of "Flet's Hikari Next" via IPv6, and DDNS mechanism is made available for easing this process (Prefixes are "semi-static", they explain). 

Now, that I knew about the service and we had an empty house I occasionally make visits to, I wanted to get the house online reasonably and at decent speeds. There, the idea of getting the house linked up with another via some kind of IPv4/IPv6 tunnel seemed like the way to go. I then decided to take advantage of c-1.) and c-2.). 
While the idea of IPsec/IPv6 (as reported successful by some) using decent routers on both ends sounded good, I also found that it wasn't reasonable enough - especially given the fact that here I am talking about activities going on in a rather "closed" network (hence "NGN" as previously named by NTT-East/West) and I was not dealing with state-level undisclosed information. Speed mattered more than the "virtually non-present" privacy issues to me. IPv4/IPv6-tunnel and GRE/IPv6 became the two choices to remain (I chose the earlier for larger MTU, but might switch soon since GRE/IPv6 could also handle IPv6 traffic in addition to IPv4).

Sitting on the "Lite" end of the service, hence the semi-empty house, is an OpenWrt box based on BHR-4GV of Buffalo, the Wired-only variant of WHR-HP-G450H. And on the "non-Lite" end of the service, hence the house I live in with IPv4/PPPoE connectivity are the Cisco 1812J and YAMAHA RTX3000. The OpenWrt/BHR-4GV now has `ipip6` connections to these two nodes respectively, and  they are set up to use BGP to exchange routing information (OpenWrt runs Quagga to serve this purpose). The throughput is being rather breathtaking, marking approximately 30Mbps(Min),95Mbps(Max), 60Mbps(Avg) for both Up and Down.

While doing this, the hard-coded values became rather problematic to me and I figured that I would  open this issue, so that users with intentions to use generic `ipip6` connections to meet their purposes would not face the same issue.
