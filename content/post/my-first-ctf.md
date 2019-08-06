+++
date = "2018-05-01T14:41:06+02:00"
draft = false
image = '/images/ctf/cyber.jpg'
slug = "my-first-ctf"
tags = ["ctf", "security"]
title = "My first CTF"
excerpt = "It was a bit unexpected."
share = false
authorbio = "Just some random thoughts."
authorwebsite = "https://tdhttt.com/"
+++

I was very excited when learning that there would be a [CTF](http://cyberctf.ics.uci.edu/) (Capture The Flag) around the campus. Upon the event went live, I registered and started to look at the challenges.

Oh, decoding binaries given some instruction opcode? Easy. Then there appears some -,+], which turns out to be an esoteric programming language called well, Brainfuck. Grab a compiler, and there you go.

Then, I was stuck when facing with a new language along with a sample function. It asked for the output for another function. Not enough information, or maybe I was not working hard enough (though it turns out nobody worked out that one).

Since I was stuck, I skipped several questions and jumped to the part that I had been looking forward to -- Web Exploitation.

## Web Exploitation

I was given a OVA for VirtualBox which serves as a http server. However, it needs username and password to login.

![Username: root; Password: root. Come on.](/images/ctf/ctf1.PNG) 

Also, when the server is running, I could get access to a webpage which also requires username and password to login in. Will the password be the same?

![](/images/ctf/ctf2.PNG)

I was very excited, trying to find useful information on the webpage. Then, I came across this comment line hidden in the html file.

> There is a room. In this room, there are two doors. One door leads to destruction, one to paradise. You have no way of knowing which is which. Also in this room are two robots. One robot always tells the truth, one always lies. There is no way to tell the robots apart. You are given a chance to ask either robot one question. What question can you ask either one that will tell you how to get to paradise?

The answer, after googling, turns out to be to ask either one, "If I were to ask the other robot which is the paradise, what would it tell me?" It got me thinking and I came up with hundreds of "smart" guessing. After an hour or so blindly guessing, I almost gave up. Suddenly, I came to this realization: the entire server is given to me and all the source files are just in the server so why don't I just focus on the virtual server?

So, I tried to go into recovery mode, get the root permission and get whatever files I want. But, no luck... Since it also asks for the password.

![](/images/ctf/ctf4.PNG)

Then I came across [this article.](https://www.vultr.com/docs/boot-into-single-user-mode-reset-root-password) Following the instruction, I opened up the boot option and appended `init=/bin/bash`.

![](/images/ctf/ctf5.PNG) 

Bingo! It worked! Here is the beautiful rooted bash:

![](/images/ctf/ctf6.PNG) 

The rest was just a piece of cake: locate the flag file and get the answer. There were even instructions on where to find the flags in the `.hint.txt`.

![](/images/ctf/ctf7.PNG)

After captured all the five flags, I suddenly came to #2 on the scoreboard. WOW. I told myself, "I am gonna win this." and went to sleep.

The rest of the story, well was not as thrilling. It turned out that the rest of challenge was closely related to crypto. And there was even a bunch of physical challenges, which also asks you to solve a puzzle.

![](/images/ctf/ctf8.PNG)

I was not really into solving puzzles, well that kind of puzzle. Also, I was pretty busy with my schoolwork. So, yes, I gave up at that point. But I started to wonder if every CTF has such a large portion of crypto. It was a bit **unexpected**.

Cover image by [AIR Worldwide](http://www.air-worldwide.com/Software-Solutions/Analytics-of-Risk-from-Cyber/).
