---
layout: post
title: Setting Up A New Computer
comments: true
permalink: setting-up-new-computer
---

So I just got a new computer for a client, and thought I'd run you guys through the series of steps I do to set up a new computer, along with notes about the current system for my own future reference.

No spoilers, but this is a profoundly dissatisfying post. If it helps, I was just as annoyed as you will be.

<!--break-->

First I log in. They gave me a MacBook Pro with an account in my name, so I logged in with the password.

Then I go to Options and turn on autohiding for the menu and the dock. I like a nice clean screen. Also turn on dark mode. My favorite color is purple, but since I can't get purple mode on a Mac (also, I wouldn't want to), I default to dark mode. Looks like this now:

![](/public/desktop.png)

Next thing is removing all icons from the dock. Nothing lives down there unless it's open in my world. Not that I ever look at the dock anyways, since I Cmd-Tab my way through open applications at nearly all times. (And I open apps with Spotlight always).

Next, I make Chrome the default browser (in this case, Chrome was already installed so I skipped the installation step).

I also add my Apple account to this Macbook so I can install Magnet, a must-have window managing utility.

Then I clone [my dotfiles repository](https://github.com/elliotbonneville/dotfiles) into `~/.dotfiles`, then cd to that directory and run `script/bootstrap` to start installing my dev environment.

Next -- actually, wait, that command failed. Bleh. Why?

It tried to install Homebrew, but that requires administrator access... which I don't have.

Yay.

Next step is to actually not finish installing my dev environment right now, since it relies on Homebrew. Instead, I quickly grab Atom so I have an editor to work with tomorrow.

I'll be back later to finish updating this post once I get administrative access and can run through the rest of the setup process.

I know, it hurts.

I'm sorry.

🐈
