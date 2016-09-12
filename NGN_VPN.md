Some might ask why this is necessary, and/or if you are curious about the backgrounds for modifying the script.

I am a happy user of OpenWrt in East Japan, whose internet connectivity is widely based on the service called "Flets's Hikari Next" by NTT-East.

The infrastructure provided by the service is rather interesting, in that the service alone merely provides the access-line, hence the L1 and L2. Although it does provide L3 via IPv6, you are given no connectivity to the WAN/Internet. By default, it's a local-WAN or Wide-Area-LAN based on IPv6. 

Getting access to the web on this service is possible by either one of the following "commercial" options;
a.)IPv4 via PPPoE
b.)DS-Lite

Primary use of such system (I imagine) is to replace the copper-line based PSTN (both analog and ISDN) by VoIP and imaginably, the monthly fee of its "Lite" service is now getting as low as those copper-line based services. There is another "interesting" use of the service, however, and this will be the main focus in this post (will be mentioned soon).

Some interesting parts of  this "Lite" service are;
a.)They are cheaper than the regular service, priced around $30/mo (around JPY3,000/mo).
***For comparison, the regular service is priced around $50/mo (around JPY5,000/mo) with unlimited download/upload.
b.)Traffic in excess of 500MBytes/mo involving PPPoE will be charged for on the pay-as-you-go basis.
c-1.)Traffic via IPv6 with no involvement of PPPoE counts only 40MBytes/mo towards the monthly usage.
c-2.)Subscribers are able to establish connections with other subscribers of both "Lite" and regular services via IPv6, and DDNS mechanism is made available for easing this process (Prefixes are "semi-static", they explain). 

Now, that I knew about the service and we had a house that we wanted to get online reasonably and at decent speeds, the idea of getting the house linked up with another via IPv4/IPv6 tunnel seemed like the way to go. There, I decided to take advantage of c-1.) and c-2.). 
I could have gone for IPsec/IPv6, but since I was not dealing with state-level secrets on WAN, encryption seemed unnecessary.

Sitting on the "Lite" end of the service, hence the semi-empty house, is an OpenWrt box based on BHR-4GV of Buffalo, the Wired-only variant of WHR-HP-G450H. And on the "connected" end of the service, hence the house I live in with IPv4/PPPoE connectivity are the Cisco 1812J and YAMAHA RTX3000. The OpenWrt/BHR-4GV now has `ipip6` connections to these two nodes respectively, and  they are set up to use BGP to exchange routing information (OpenWrt runs Quagga to serve this purpose). The throughput is being rather breathtaking, marking approximately 30Mbps(Min),95Mbps(Max), 60Mbps(Avg) for both Up and Down.

While doing this, the hard-coded values became rather problematic to me and I figured that I would  open this issue, so that users with intentions to use generic `ipip6` connections to meet their purposes would not face the same issue.
