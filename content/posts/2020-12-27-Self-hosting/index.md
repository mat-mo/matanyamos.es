---
title: "Self hosting"
description: I self host my data for many years, you should as well
date: 2020-12-27T12:57:55+02:00
tags: ["Self hosting"]
categories: ["Freedom"]
authors:  ["Matanya Moses"]
slug: "2020-12-27/self-hosting"
---

I have been self hosting my mail since 2011, over the years I added more data types. The reason I have been self hosting is because I like to own and control my data, and my dislike for sharing my data with Google/Microsoft/Apple and other companies. In this post I am going to share with you my setup, but of course, it is tailored to my needs, and may not suit yours.

{{< figure src="ynh_logo_black_300dpi.png" caption="Yunohost Logo, CC by-sa-4.0" >}}

## Server and OS

In the beginning of my self hosting journey, I have built a server at home,
since I didn't find a cost effective and easy to use VPS provider at that point
in time. I called my ISP and asked for a static IP, which I got, for 3$ per
month. This allowed me to buy a domain and route traffic to my static IP. 

I have set up the server with Debian (And it is still running until this very
day) and added [Yunohost](https://yunohost.org) on top of it. The main
disadvantage to that setup was my ISP refused to set up PTR record for reverse
lookup to point at my address. This gave me low marks on email scoring systems. 

I lived with the setup for several years. I have been debating whether I should
migrate to digital ocean or a similar provider for some time, but then
[lightsail](https://aws.amazon.com/lightsail/) was announced, and I knew I want
to use it. The migration was fairly easy, I just took my mailbox and imported it
on the new server. 

## Software
### Mail

The backend setup didn't change since creation. It is the basic backend delivered by yunohost. For the frontend, I used roundcube at the beginning, but then moved over to rainloop. I didn't like the lack of integration between rainloop and a calendaring application, so I decided to move to Sogo. I stayed with Sogo for
several years, until I had to find a solution for my pictures, movies and other
files. Then I moved to Nextcloud.

### RSS Reader

As mentioned, I used to host my mail, but over the years, I moved more and more
things to my self hosted platform. The first addition was in 2013, when Google
announced google reader is being sunset. I really liked the product, and wasn't
too sorry when it went, because it forced me to re-think where I should host my
RSS reader. I decided to use [tt-rss](tt-rss.org) at first. It was comfortable
and easy to use. However, the mobile interface user experience was lacking, and
I decided to migrate to something else. I moved to [Fressrss](https://www.freshrss.org), which was really great. I stayed with it for several years and would have stayed with it if Nextcloud wouldn't have a really great RSS reader. I always prefer to maintain less software, even if it violates the unix way of doing one thing, and doing it well. 

### Nextcloud

As the use of smartphones was getting more and more common, and the fact Android and iOS default to sending data to Google/Apple respectively, I figured it was time to re-think my entire self hosting platform. After some thinking, testing and benchmarking I decided I should use [Nextcloud](https://nextcloud.org) as my sole platform for storing my data. I use Nextcloud to store my files, mainly photos and movies taken by my family over the years, but also documents that used to reside on google drive, and my personal music that used to be on a NAS. In addition, I added the mail app, and the news app from the Nextcloud store.

I have configured our smartphones to upload images taken by our cameras to our Nextcloud instance running on our Debian + yunohost server. And took out any data that was stored on Google using [Google takeout](https://takeout.google.com). 

I didn't want to store our data on EBS drives, and it is not so durable compared to other services, and much more expensive. I decided to use the S3 external storage feature in Nextcloud, on order to get low cost, high durability for our files. 

As a matter of fact, I added the calendar, talk, contact and audio player apps as well, in order to cover for a good calendaring app, a communication app instead of meet/whatsapp/telegram/signal/hangout etc, contacts instead of google contacts my phone was using by default, and the audio player to play my music. 

This setup basically covers all my self hosting needs in terms of private data.

### Blog

I have been using Medium for writing this since 2019. But I didn't like the fact my posts are stored by someone else. As a result, I installed wordpress to host my blog, as I thought that would be the most straightforward and easy thing to do. After thinking about it for a few minutes, I realized it wasn't a great move. First, it amplified the attack vectors on my server with a public facing service. Second it did so with a not very secure application (sorry about that wordpress). So I decided it is time to think about a static site generator. I looked around and figured Hugo is a good choice for me. This way, I host my files on S3, and not opening my server for public access, with an insecure application. Amazon since announced AWS amplify that simplified things further. Now I just commit to git, and everything is handled from there.

For the most basic tracking I have setup Matomo, just so I know what people
actually read, and what I write simply for myself. 

### IRC

Yes, I am still active on IRC. I use The Lounge for that. Very east and convenient solution for remaining always on on IRC, and solving the need to go for services like irccloud and similar offerings.

## What is left to do
### Linkedin

The only service I didn't really replace is Linkedin, I don't know what to do with that. I don't use any social networks, so no Facebook, Twitter, VK etc, the only exception is Linkedin, the reason I am there is I treat it as a workplace tool, but over the years, I see less and less value in it. I might just drop it at some point and say goodbye.

### Git server

Git is also an open point. I keep most of my stuff on github. I do think I might need to move from github to a personal hosted gitlab, once I find the time and energy. The sole reason I am on github is the fact it is easy to collaborate this way, which is not the case on a personal owned instance, if I move my personal only things, which I don't collaborate on, that would be a good first move. It will also help if AWS amplify would support private git servers, and not only public github and gitlab services. But that would probably be some work for the futuer. 

## Cost

To close this piece, you are probably wondering what is the monthly cost of such a setup. The annual cost for a domain is 12$ or a dollar per month. The server cost is another 10$ per month, per the instance type I picked, S3 is another 3$ per month. AWS amplify is 1 cent per build-minute of the site, so several cents per month, depending on my publishing frequency and build time. All in all, 14$-15$ per month, nothing really big. More or less similar to the cost of buying additional storage from Google/Apple when you exhaust the default free storage. 

Maybe not for everyone, but worth a thought a least. 

---
