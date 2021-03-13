---
layout: default
title: CTFd
nav_order: 2
has_children: true
permalink: /docs/CTFd
description: "CTFd description Docs"
---

# CTFd Docs
{: .no_toc }


CTFd는 Capture The Flag 프레임 워크이며 각종 CTF 대회에 쉽게 하용할 수 있도록 만들어졌습니다.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

[CTFd Github](https://github.com/CTFd/CTFd)

[Live Demo CTFd](https://demo.ctfd.io/)

<br>

---

<br>

![CTFd logo](/post_images/CTFd/index/logo.png)

<br>

+ ## Features
    + Create your own challenges, categories, hints, and flags from the Admin Interface
        + Dynamic Scoring Challenges
        + Unlockable challenge support
        + Challenge plugin architecture to create your own custom challenges
        + Static & Regex based flags
            + Custom flag plugins
        + Unlockable hints
        + File uploads to the server or an Amazon S3-compatible backend
        + Limit challenge attempts & hide challenges
        + Automatic bruteforce protection
    + Individual and Team based competitions
    +     Have users play on their own or form teams to play together
    + Scoreboard with automatic tie resolution
        + Hide Scores from the public
        + Freeze Scores at a specific time
    + Scoregraphs comparing the top 10 teams and team progress graphs
    + Markdown content management system
    + SMTP + Mailgun email support
        + Email confirmation support
        + Forgot password support
    + Automatic competition starting and ending
    + Team management, hiding, and banning
    + Customize everything using the plugin and theme interfaces
    + Importing and Exporting of CTF data for archival
    + And a lot more...