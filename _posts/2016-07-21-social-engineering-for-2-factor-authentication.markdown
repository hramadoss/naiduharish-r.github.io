---
published: true
title: Social Engineering - For 2 Factor Authentication 
layout: post
---
Recently on a social engineering assessment, we created a fake OWA(Outlook Web Access) page and sent it out to a few employees with a scenario saying "we have made a changes to mail infrastructure, please login blah blah ...." This scenario works for me 90% of the time and we end up with domain credentials. From here it is easy, you login into there OWA account get access to their contact list, loot more sensitive information and further plan your attack...sweet!!!

However this time we faced with a scenario where the client was using two factor authentication - So first employee would enter his domain credentials to login to their OWA account and then an OTP is sent to registered phone number. The user needs to enter the OTP on second page. 

So now in this case although we had a few valid usernames and passwords, we couldn't login to the OWA since we needed the OTP....Mann!!! 

So at this point we could get a sweet lady who can call the user and somehow lure the user to give the OTP, but this needed a sweet lady and the user who can get lured...possible but too much work to do :(

But  now since we know how the second page looks like(OTP Page), remember we got a few valid credential from victims who entered their credentials. We quickly made two pages -  OWA login page which upon submission redirects to our fake OTP page.

We can now send the the login link to a few more users, hopefully they will enter valid user credentials. As soon as they enter valid credentials we need to either manually or using a script(CURL Request) submit this to the actual OWA login page. Since we submitted the credentials, the user now gets the OTP. We take this OTP and once again submit it on the actual page. Boom we now have access to the victim account although they had two factor authentication.

I have tried to explain the above using a flowchart. Please excuse if the flowchart confuses more :)

[id]: https://raw.githubusercontent.com/hramadoss/naiduharish-r.github.io/master/Screen%20Shot%202016-07-21%20at%2011.19.13%20AM.png "Two Factor Authentication Bypass"