---
layout: title-page
title: "IPFS Desktop Demo"
permalink: /class/02-IPFS
---

<!-- IPFS CIDs for websites can be found via: https://docs.ipfs.io/concepts/dnslink/ -->

An introduction to IPFS via the Desktop application.
_Ideal for those new to IPFS._
**Following along from the [workshop slides](https://docs.google.com/presentation/d/1Nrwece33ElfVB5ibyvloQX80kZFmUpkLHdvGTsKu-PI/)**

---

## Install IPFS Desktop

Now is the time to get IPFS Desktop! Instructions are available for Linux, Mac and Windows:

#### <https://docs.ipfs.io/install/ipfs-desktop> 

---

## Import and Serve a File via a Local IPFS Node

Let's all use the _**same file**_ to start: 

The <a href="https://ipfs.io/ipfs/QmZq1igrmuyfHeEpWLqeRMvpBRMU2a8nGqEdAQGHxV7yt4/blockchain-at-berkeley.png"><b>B@B Logo</b></a>:
<br>
<center>
<img width="250px" src="https://ipfs.io/ipfs/QmZq1igrmuyfHeEpWLqeRMvpBRMU2a8nGqEdAQGHxV7yt4/blockchain-at-berkeley.png"> 
<br>
</center>

Right Click and download ("save link as...") the image above, so we can play together!

---

## Open IPFS Desktop and Import Files to your Node

Navigate to the "Files tab" and hit "+Import" and select the `blockchain-at-berkeley.png` file we just downloaded.

FIXME -- SCREENSHOT NEEDED

After you import...

FIXME -- SCREENSHOT NEEDED

You should see the file has a funny subtitle starting with `Qm...` - **This is the CID of the file!** 
Let's take a deeper look at this file by **inspecting it**

FIXME -- SCREENSHOT NEEDED

Here we can see that this file is very small (8 KB) and thus all the data for it can be contained in **just one chunk**! Our `Object` has all the `Buffer` data it needs to reconstruct the file directly.

FIXME -- SCREENSHOT NEEDED

---

## View Your file on Your Node's Gateway

Now that ***your*** node has a copy of this file, we can view it via our **local IPFS gateway** - this is a **HTTP server for IPFS**. So we can use this *webpage* to interact with IPFS!

IPFS-desktop will, by default, bind the gateway to `http://localhost:8080/` on our local machine. We can query IPFS content by CID through the desktop interface

FIXME -- SCREENSHOT NEEDED

Notice the URL (one of two versions, both are the same with different _encodings_ of the CID): 
- <http://127.0.0.1:8080/ipfs/QmRNLiyC3EykbePXT6XULZjDrKZQyZ2ku5qtALkDW96V4E>
- <http://bafybeibnahrpkvbhk6okv5ws3fkyhzkmem3jwfiokogwyacjk7xgc6fgsm.ipfs.localhost:8080/> 

This tells us that we are in fact looking up via _our local machine (127.0.0.1 or localhost)_ and querying for **data with a given IPFS CID** of the (preferred, newer format) format `http://<YOUR-CIDv1-HERE>.localhost:8080/`

---

## Ask Another Peer to Retrieve Your File

We can ask _another_ IPFS node out on the wild web if they can see it! There are many **public** [**IPFS gateways**](https://docs.ipfs.io/concepts/ipfs-gateway/#overview) that our fine friends host, and can be [found here](https://ipfs.github.io/public-gateway-checker/).

Let's see what we find if we ask the https://ipfs.io gateway to retrieve our file's CID. In much the same way, we just need to specify the right CID to retrieve:

- https://ipfs.io/ipfs/QmPHruLBfdnqMDh1emvVZY7UdK5ShLrLi5qtFnA2x27Q1M 
- https://bafybeiaoes5vkw53bmxh7iw62ml2t36zjqgtlwh3o2odzonqbeyhpknhoa.ipfs.dweb.link/

Open up those links and see what you get! 

FIXME -- SCREENSHOT NEEDED

Sweet! The file is found by the ipfs.io _and_ dweb.link nodes via _different encodings **and** different methods!! This confirms that not _just our local node_ knows about this file - our peers can get it too!! And in a _various of ways_.

***Notice we didn't upload this file anywhere! The IPFS network was able to retrieve it from OUR NODE!!!***

... well kinda... this is a bit of a silly example: the file you downloaded above came _directly from this IPFS gateway to begin with (check the link URL above WHERE WE DOWNLOADED IF FROM)_.
What it _does_ show is that you got the exact same CID for the same file.

!!! **This is an important note:** 
- We know that our node chucked, and served the example file just as any other IPFS node would.
- This also means **our node is now (by default) also willing to serve this file (and it's chunks)** 
    - This is not only via our gateway, but directly through Peer-to-Peer (P2P) communication between other IPFS nodes!

So by following along here - you just advertized your node (by your *peer ID*) to other nodes you are connected to that you have and will share this data ... if they ask nicely ;)


---

## Peer Connections and Data Sharing

What?! You mean to say that I already am sharing this data with many different people all over the world from my node? [^1]

**YES**

[^1]: By default, yes. Only if you [**pin**](https://docs.ipfs.io/how-to/pin-files/) this data (file upload does this automatically). But this data will only be shared if other peers know the CIDs for content you hold and request it. And only if your machine is on a network that can connect *out to other peers* - and many firewalls and NATs don't always play nice with this.

You can see a list of the peers that you are directly connected to on the `Peers` tab:

FIXME -- SCREENSHOT NEEDED

Without going into the weeds on the details of _how_ your node goes about sharing and finding data on the IPFS network (but you totally can [here](httpshttps://docs.ipfs.io/concepts/dht/) after the workshop) we experiment with **asking your peers for some data directly**.

We don't need for a gateway (a **single** node out there somewhere) to gather all the chucks we need for some data - we can ask our peers for them!

---

## Request content via CID

On any IPFS Desktop tab, at the top, you will see a search bar. Go ahead an put this CID into it:

`Qmdgqdddt3F2uszEaE7zph7kXbwHX3iTDCWeQjdtNGnQgz`

You will likely need to _download_ this file if no preview is available. Note the proper extension for the file is `.jpeg` (it may not come with one or the wrong `.txt` extension, so add/change it if so)

What do ya see when you **open this file**???

_NOTICE: No DNS or HTTP required! This was found directly on the IPFS network! The CID was all we needed - not a URL!_ 

This fine photo is from a set of Apollo program photos and happens to be famous - you seen it before? This is one of many that are available on IPFS!

Wouldn't it be awesome if you could browse **a website album** of all these _on IPFS_?[^2] 

[^2]: Here is the _same_ photo in the Apollo archive album: http://127.0.0.1:8080/ipfs/QmSnuWmxptJZdLJpKRarxBMS2Ju2oANVrgbr2xWbie9b2D/albums/QXBvbGxvIDEwIE1hZ2F6aW5lIDM1L1U=/21328560323_6b33f5d4c3_o.jpg 

**YOU CAN!**

---

## Browse IPFS Static Website content 

[Static Websites](https://en.wikipedia.org/wiki/Static_web_page) are, as the name implies, consisting of _unchaining data_. There is no need for a backend server somewhere that must _construct_ some data _dynamically_ every time we want to view or use a web application.

Static sites are just a set of HTML, CSS, and JS files... **so once created, we can *host* static sites on IPFS!!** 

To see this in action, the let's checkout a static web album **with our IPFS Desktop app open (so our node is running)**, click here:

### [Apollo Photo Archive](http://127.0.0.1:8080/ipfs/QmSnuWmxptJZdLJpKRarxBMS2Ju2oANVrgbr2xWbie9b2D/frontend/frontend.html)


**Notice the URL... *its local!***

FIXME -- SCREENSHOT NEEDED

So... our node behind the scenes looked up a CID and from this was able to construct the site... **locally**. Our peers delivered the content, and now we can browse the site... **even offline** (if we pin the site to our node) and will share the site's content with any peers that ask for it!

_By using and IPFS node to pin static websites, you are acting as a server for some or all of the content for the site on IPFS!_

...

So what if I wanna ***publish an IPFS website*** and have others help share it and keep it alive... even when my node is offline?

### _Back to the [workshop slides](https://docs.google.com/presentation/d/1Nrwece33ElfVB5ibyvloQX80kZFmUpkLHdvGTsKu-PI/) for more!_

<!-- ---

## Future content...

TODO

Static Website Deployment 
1. manually locally
2. via a pinning service (pinata)
3. via Fleek


Use-case examples:
* Serverful infrastructure - when everything is a server
* Local first collaboration - disconnected subnet, airplanes
* Censorship resistance - contextual threat models
* DDOS resistance -
* Service EOL - business dies, is bought+closed -->

---

## _Footnotes_

<!-- auto generated from above -->