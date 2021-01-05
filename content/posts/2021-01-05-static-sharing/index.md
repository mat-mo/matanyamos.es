---
title: "Share files with Grandma using git"
description: "A short tutorial on sharing large files without installing
anything on grandma's computer, using git"
date: 2021-01-05T14:55:27+02:00
tags: ["webtorrent", "github", "static site", "git"]
categories: ["Technology"]
authors:  ["Matanya Moses"]
slug: "2006-01-02/static-sharing"
---

## Can I share large video files of my kids with grandma?
This is a question a friend of mine asked me. 

I was sure he was kidding. I said: "sure! Use google drive, or S3 or any large
file storage provider and give her the link".

Then he came with some requirements that made the initial ask somewhat more
complicated. 
## The requirements
* Should not cost money, not for my friend and not for his grandma
* Should not be uploaded to the cloud
* Grandma won't need to install anything, preferably use a browser only

I was somewhat puzzled. If he doesn't want it to cost money, this means his own
server is off the table. So nextcloud is not an option.

Not uploading the files means services that host your files are off the table
too. So no google drive, no S3, no mediafire, no we transfer, not even github. 
This meant she had to get the files directly off my friends computer.
The only reliable way I knew to do that without installing anything are services like
[sharedrop](https://www.sharedrop.io/), but they only work on the local network.
It can be done with other protocols, like ftp, bittorrent and others, but that
would violate the third requirement. At this point, I was about to tell him it
is not doable. However, after giving a bit more thought, I came to a solution. 
## The Solution 
I figured torrent is the best option, but wasn't sure how to get that into the
browser. Since requirement number 3 prevents the installation of additional
software, and I am sure my friend would not enjoy teaching his grandma to use
torrents, that would be long, tedious and will likely fail, it had to be in the
browser.

I remembered the [webtorrent](https://webtorrent.io/) project. This would solve
my issue of bringing torrents to the web, but didn't solve the issue of not
uploading the file somewhere. It basically meant my friend needed a way to
create the torrent and then share the torrent file on a web page. 

Creating a torrent and putting it in a git repo means I don't upload the file to
the cloud, only the torrent file. Pushing that into github opened the ability to
use github pages. This meant all I need to do is add some code to have a
javascript based player, and the torrent file in the repo. After another
thought, I figured I don't even need the torrent file, and can just put a magnet
link in my html file. Here is a [demo page](https://mat-mo.github.io/shooroo/)
I created to demonstrate it. 

{{< figure src="shooroo.png" caption="Screenshot of the demo site" >}}

I have a laptop running webtorrent at home, which basically seeds the files on
the page above in the webtorrent protocol, which is just a regular torrent
protocol with the transport part using webrtc instead of tcp or udp. 
A side benefit of this is the fact ISP's don't throttle this kind of traffic, as it
looks like webrtc communication, and not torrent communication. 
## Outcome
I told my friend to use [webtorrent desktop](https://webtorrent.io/desktop) so 
he won't need to run node and npm for the CLI version I used. It is a simpler
way to create the torrent from the file and magnetize it. 

After my friend did that, he was very happy with the outcome, but came with
another ask, can the files be private? I didn't think about a good solution to
this one yet, but I think if he would agree to [self
host](https://www.matanyamos.es/posts/2020-12-27/self-hosting/) and pay a few dollars a
month I would recommend setting up a private
[peertube](https://joinpeertube.org) instance. 

---
