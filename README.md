# OEHU Documentation

_All you need to know about the OEHU project._

OEHU gives you the option to really own your energy data. Simple connect an OEHU enabled device to your smart meter. From this moment you'll have access to both all raw data and a nice, own personal dashboard.

## Project setup

For this project we have created multiple things. Below an overview.

### Visual design

We have created a visual identity for OEHU. Find images, website design & flyers/posters in the [oehu-identity](https://github.com/OEHU/oehu-identity) repository.

### Website

We have a website for [project information](https://oehu.org/), [onboarding](https://oehu.org/setup) & data dashboards.

- Find the website code at https://github.com/oehu/oehu-website
- Find the website build at https://github.com/oehu/oehu-website-build.
  - The website is auto deployed by using [netlify.com](https://www.netlify.com/) 

### BigchainDB nodes

We have set up 4 bigchain db nodes, running on DigitalOcean VPS's. We might add documentation in the future.

### OEHU API

We have created the [OEHU API](https://github.com/OEHU/oehu-api) for making it easier to query bigchaindb.

The API connects with one of the bigchaindb nodes using `ssh root@IP -L 27018:localhost:27017`.

### OEHU WiFi Setup

You'll connect a Raspberry Pi (or similar micro computer) to your smart meter. For this 'OEHU enabled device' we created some software.

One of the things we created is the [oehu-wifi-setup](https://github.com/OEHU/oehu-wifi-setup). This script creates a WiFi hotspot, 'OEHU Setup', that you can connect to from your laptop. Next you can select your own WiFi-network & your OEHU device will be running in no time!

### OEHU Setup API

At the setup you'll go to https://oehu.org/setup - to register some basic info, for creating a login & to start registering energy data.

The website interacts with the OEHU device via the [oehu-setup-api](https://github.com/OEHU/oehu-setup-api). Find information about all possibilities in the [README](https://github.com/OEHU/oehu-setup-api#oehu-setup-api).

### (P)Research

In the [blocklabnl/VEL](https://github.com/blocklabnl/VEL) Max did the first part of research on -mostly- bigchaindb. Find documentation, tests and examples here.

We created a project plan and defined bounties using [issues](https://github.com/blocklabnl/VEL/issues) in combination with [gitcoin.co](https://gitcoin.co/). You'll find the contributors on this project below.

### Community channels

Become part of the community by joining one these channels:

- [Telegram](https://t.me/joinchat/A8b03hI61nBIbnVF18582A)
- [Twitter](https://twitter.com/oehu_project)
- [LinkedIn](https://www.linkedin.com/company/11865484/admin/overview/)
- [Newsletter](https://oehu.us19.list-manage.com/subscribe/post?u=ab502529571629d74b3510e56&id=dacb068b56)
- [GitHub](https://github.com/OEHU/)

## Contributors & Sponsors

Thanks to all [contributors](https://github.com/orgs/OEHU/people).

- [bartwr] - concept, coordination, development, communication
- [ilhanu] - initiator, concept
- [Jaron] - visual identity, together with StudioSpass
- [mfahampshire] - concept, bigchaindb node setup, development
- [liamzebedee] - testing of bounty platforms
- [marijnbent] - design, development
- [Marlow] - development
- [MickdeGraaf] - development
- [Sus4nne] - documentation, communication, testing
- [Hansie020] - testing

Without our sponsors this project wouldn't be made reality.

- [BlockLab](http://blocklab.nl/)
- [Metropoolregio Rotterdam Den Haag](https://mrdh.nl/)

Interested in sponsoring? [Send us a message](https://www.bartroorda.nl/contact).
