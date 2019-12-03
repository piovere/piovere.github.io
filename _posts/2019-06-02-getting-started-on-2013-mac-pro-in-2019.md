---
layout: post
title: "Getting started on a 2013 Mac Pro"
date: 2019-06-02
---

Recently a friend of mine upgraded from a trash can Mac Pro to an iMac Pro. 
He then generously offered me the old trash can as he didn't seem to think 
that he had any use for it. Being the giant nerd that I am, of course I said 
yes.

I've been wanting to get my hands on a Mac Pro since shortly after I started 
listening to [ATP](https://atp.fm/). Before that, I (who had grown up on the 
PC side of the world) didn't understand the appeal of these machines--I 
counted the GHz and RAM and couldn't understand how one could justify the 
cost jump for those machines. As I listened to @siracusa speak though, I 
remembered my two experiments with hackintoshes--how everything required 
constant troubleshooting just to keep working. I wanted the opposite of that. 
I wanted everything to "just work".

So yeah, I jumped at the chance. My career is taking me further and further 
down the machine learning path combined with some modeling code that scales 
across CPU cores and I knew two things about the Mac Pro: lots of cores, two 
GPUs. Surely I could make something work?

What I should have done was remember that those GPUs and Cores were fancy...
 in 2013, when the Mac Pro was released. Sure they had been bumped since then 
but the 'ole "thermal corner" was coming to bite me. ROCm (the acceleration 
framework[^1] for machine learning on AMD GPUs) only runs on cards newer than 
March, 2014. So there went my plans of booting into Ubuntu for some somewhat 
accelerated GPU training[^2].

So in the meantime I've just been enjoying the mac-ness of the machine. It 
really is a no-drama experience. I don't know how I could use all of the 32g 
of RAM yet, and 6 cores matches my MBP, but without battery concerns. At the 
very least it's going to be a great replacement for the limping-along 2012 
Mac Mini that currently handles anything I need to run at home over long 
stretches.

[^1]: Go ahead and @ me, I need to learn this stuff.
[^2]: I have actually been poking at PlaidML and that might help. I see about 
5x speedup on their benchmark test, but I haven't put any of that into the 
world yet to see if that matches real life. I'm also really looking forward 
to them adding multiple GPU support, which should mean another speedup.
