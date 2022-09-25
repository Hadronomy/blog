---
title: DIARIES - Configuring an email server with IMAP and POS3
date: 2022-09-25 21:16:39
tags: [postfix, linux, begginers, tutorial]
categories:
- [tutorial, diaries]
---

## Introduction

Just recently I had to setup an email server for my own personal use. Along the way I learnt many things and encountered multiple problems.

So, after finally getting it up and working, I'm documenting the whole process for your and my own personal use.

## Why an email server?

There are a lot of services that offer business email addresses (Google, Microsoft, etc..). But often you have to pay for each email address you create and while it offers some nice features, you end up paying more than you should.

By setting it up yourself, you can customize it to your heart desire and just pay the server hosting.

> Which in Digital ocean, what most people would need it's just 4€ a month. And if you want a little more it's just 6€

## That's all nice and that.. but How?

Well, first of all you will need at least a basic understanding of linux and be more or less comfortable with `ssh` and the command line.

That said, I'm going to use **[DigitalOcean](https://m.do.co/c/79c690119404)** to host the server. You can use any other service that you like ([Linode](https://www.linode.com/es/) for example).
> If you don't have an account don't worry about the price, at the start you are given 100$ of free credit

As for the email server itself, we will primely use a very known linux package: **[postfix](https://www.postfix.org)**.

But most importantly, **you need to own a domain**. If you don't, you can buy one from your registar of choice (Google, GoDaddy, Namescheap and others).

## Hosting the linux server

First of all you will need to [create an account](https://m.do.co/c/79c690119404) if you don't already have one.

Now with your account created, you should see something similar to this
![Dashboard](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/g9oqsvuns7l4uovr54fx.png)

If you want to, you can check all the things that DigitalOcean offers. We are going to use **droplets**.
![Create droplet](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/imdbvgz5gdw74gmqincu.png)

![Droplet creation screen](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rl3qcucmnjgi50jp858q.png)

For this setup we are going to use Ubuntu.
![Choose distribution section](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iz441n5205v1e9wihrfz.png)

And for now the cheapest one is good enough. If you want, you can later upgrade the droplet to higher specs.
![Choose specs section](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/97qt9ycbqtbxgw2rg9e0.png)

For the droplet location choose whatever you want. In this case I'm choosing the one closer to my location.

![Choose location](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0194kx2ffq68qa01ll9p.png)

In the authentication section, choose your already added ssh keys or add a new one.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bc78d3437zl071wl3bfj.png)

If you want to add a new one, just click the "New SHH Key" button. In the popup dialog you will have all the instructions required to do so.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uks6dj2thgpfdab01biy.png)

As for the name of the droplet, for now, you can leave it as it is.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sm1thoksjqzum3ibowu3.png)

Finally you just have to click this wholesome button.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h0mh7pvpl59x2tn0mwau.png)

We now have a lovely droplet :smile:
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rycvy3iid6yffufvv53e.png)


## SSH it!

```bash
$ ssh root@<droplet-ip-address>
```