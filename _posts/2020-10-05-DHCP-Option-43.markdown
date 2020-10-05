---
layout: post
title:  "DHCP Option 43 with Unify phones"
date:   2020-10-01 17:00:00 +0930
categories: [work, dhcp]
---

Let me preface by saying I'm not an expert on VoIP Phones (or DHCP Options) in any way.

To keep things short, DHCP Option 43 allows you to specify Vendor Specific options, for example configuring IP phones with an address for a DLS Server. The DHCP server that would be serving addresses for these phones is on a switch whose configuration is done entirely through the CLI. At first I thought no big deal, but long story short I ended up constructing a hex value which the switch would pass on to the phones. I ended up with something like this in the DHCP configuration:

`option 43 hex 01075369656d656e73020400000065031a73646c703a2f2f39332e3132322e3131342e39363a3138343433ff`

Now the fun part is how that string is constructed. The [Unify Documentation][unify-doc] goes into more depth, but the guts of it is that the hex value contains the string 'Siemens' (the vendor string), the VLAN ID and the address of the DLS Server.

- Siemens : `5369656d656e73`
- 101 : `00000065` (convert decimal to hex)
- sdlp://93.122.114.96:18443 : `73646c703a2f2f39332e3132322e3131342e39363a3138343433`

However, what I didn't realise is that you need to specify the tag and length before each value. The [Unify Docs][unify-doc] has each of these values, but for an example `5369656d656e73` turns into `01075369656d656e73` (tag 01, len 07). I did this for the other 2 values, and ended the hex value with `ff` as specified by the docs, and voilà, the phones work!

[unify-doc]: https://wiki.unify.com/wiki/VLAN_ID_Discovery_over_DHCP
