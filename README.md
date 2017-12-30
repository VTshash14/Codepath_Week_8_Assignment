# Week 8 Project: Pentesting Live Targets

Time spent: 2 hours spent in total

> Objective: The challenge is to attempt to find and exploit the vulnerabilities. The goal is to identify which two vulnerabilities of each site: red, green, and blue.

The following **required** functionality is completed:

1. [X]  Required: Challenge 1 - Username Enumeration
1. [X]  Required: Challenge 2 - Insecure Direct Object Reference (IDOR)
1. [X]  Required: Challenge 3 - SQL Injection (SQLi)
1. [X]  Required: Challenge 4 - Cross-Site Scripting (XSS)
1. [X]  Required: Challenge 5 - Cross-Site Request Forgery (CSRF)
1. [X]  Required: Challenge 6 - Session Hijacking/Fixation


## Challenge 1: Username Enumeration
- Vulnerability Site: Green
- Vulberability: If you enter in the name of a known user like jmonroe99 and a random password,  you will recieve an error message.  The error message is bold, but if you enter in a random username like hokie1 and a password it is not bold.  The programmer indicates found users by making their unsuccessful logins bold, which can be exploit.

Here's a walkthrough of implemented vulnerability:

<img src='https://i.imgur.com/bzucNdZ.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).


## Challenge 2: Insecure Direct Object Reference (IDOR)
- Vulnerability Site: Red
- Vulberability: You have a screen of salepeorsons and their territories on each site.  
The Sales Peorson Names and ID:
  - ID=1 NAME: Daron Burke
  - ID=2 NAME: Sherry Trevino
  - ID=3 NAME: Irene Boliing
  - ID=4 NAME: Robert Hamilton
  - ID=5 NAME: Ken Barker
  - ID=6 NAME: Elizabeth Olson
  - ID=7 NAME: Samuel Hunter
  - ID=8 NAME: Kim Stanley
  - ID=9 NAME: Barbara Hinckley
  
  - ID=10 NAME: Testy McTesterson (NOT PUBLIC)
  - ID=11 NAME: Lazy Lazyman (FIRED)

On the red site if you enter in the numbers 10 and 11 in the url, you are able to see Testy McTesterson and Lazy Lazyman who are not visible on the Green and Blue sites. The programmer did not disable those users on the red site leaving the IDOR vulnerability.

Here's a walkthrough of implemented vulnerability:

<img src='https://i.imgur.com/2ytMuPu.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).


## Challenge 3: SQL Injection (SQLi)
- Vulnerability Site: Blue
- Vulberability: Sanatizing your data is very important when using SQL databases, but the salesperson information for the blue site does not sanatize the data for the name and feedback fields.  Attackers can exploit this and in our case we will use the command %27%20OR%20SLEEP(5)=0--%27 when setting the ID.
    This causes the page to take 5 seconds in fetching the data and defaults back to the first user David Burke with ID=%27%20OR%20SLEEP(5)=0--%27.

Here's a walkthrough of implemented vulnerability:

<img src='https://i.imgur.com/3w8xezW.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).


## Challenge 4: Cross-Site Scripting (XSS)
- Vulnerability Site: Green
- Vulberability: The problem with the green site is that if you create an alert message and insert it into the the comments section you will see the alert message every time you click on the contact messages in your nonpublic screen.
The alert message: <script>alert(’     found the xss exploit');</script>

Here's a walkthrough of implemented vulnerability:

<img src='https://i.imgur.com/Pe4nTwD.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).


## Challenge 5: Cross-Site Request Forgery (CSRF)
- Vulnerability Site: Red
- Vulberability: If you create a malicious page that utilizes the user's session to forge a request to the database. That page will make a request during the page loading and hides the page.  When you return to the sales list you will see the changed salesperson.

Here's a walkthrough of implemented vulnerability:

<img src='https://i.imgur.com/vw0XxCM.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).

## Challenge 6: Session Hijacking/Fixation
- Vulnerability Site: Red
- Vulberability: The SessionID is not secure and the contents of the packet are forwarded to additional sites. I was able to login in to the red site and also be logged in to the blue site without actually logging into the blue site.
Here's a walkthrough of implemented vulnerability:

<img src='https://i.imgur.com/Lq3p0Jw.gif' title='Video Walkthrough' width='' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).

## License

Copyright [2017] [Shashank Shinde]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.





