---
layout: post
title: "A Series of Unfortunate Events"
headline: "Have you ever failed so hard you almost gave up of your entire career?"
description: "Have you ever failed so hard you almost gave up of your entire career?"
modified: 2015-12-07
category: consulting
imagefeature: "covers/a-series-of-unfortunate-events.jpg"
mathjax: 
chart: 
comments: true
featured: true
---

This may be unusual, but I want to start my first post about experiences as
a freelancer not with tips, but talking about a mistake. Not actually A
mistake, but A Series of Unfortunate Events.

It all started well, as most of the stories do. I was new on Codementor, and I
had been mentoring a client, helping him build a Rails project, and we got to
the part where we needed to deploy it to Heroku.  As you may know, it's not
possible to store uploaded images in a Heroku app as you would in a regular
server, due to its [ephemeral
filesystem](https://devcenter.heroku.com/articles/dynos#ephemeral-filesystem)
(to be honest you can, but you shouldn't), so I went ahead and started showing
him how to configure the S3 upload for the Paperclip gem. We were having some
trouble with the Zoom.us application, it wouldn't let me take remote control
over my client's machine, but since I wanted him to be able to reproduce
everything later, I thought it would be nice to guide him instead of merely
explaining everything as I was doing the work (silly, inexperienced me). So
there we go, IAM Users, access and secret keys, bucket configuration, group
permissions, environment variables and security explanations, gem
configuration. One hour and a lot of confusing steps later, we were ready to
run the application. Except it wouldn't run.

That's when everything started to go wrong. I don't remember exactly what the
error was, but at the time I was sure I had seen it before, so I confidently
walked him through the debugging session, then we tried again. Same error. Time
after time, my proposed solutions wouldn't work. I was getting nervous, but was
determined to fix it. Then, suddenly, he told me that he had a deadline (why he
didn't tell that before?), and now he was in a worse position than in the
beginning of the session, since the project wouldn't run anymore. "Can we erase
everything and go back to how it was two hours ago?". I immediately felt a
horrible cold in my stomach. You see, before we started configuring S3, we had
implemented some features, but didn't commit them yet. "I screwed up.", I
thought. "I've let down a client to the point where he prefers to lose
everything that we did".

After asking if he was sure of that, I've made a terrible decision: I wanted
him to be able to keep the code we had written earlier, but since I was so
nervous and couldn't think straight, I decided to commit those changes, push them
to the remote repository on Github, then erase them from local so he could try
again. Sounds a bad idea? It gets worse.

Panic do weird things to you. Not only you make bad decisions and feel
paralysed; you also forget even the simplest, most basic pieces of knowledge.
For example, the <code>git revert</code> command. So, there was I, guiding with
only my voice an inexperienced programmer on deleting a previous commit on git.
When I think about it, I actually thank God that I didn't make him lose his
entire repository.

At this point, I could see despair in his eyes. He came up straight to me and
said that he couldn't afford wasting more money, and asked to end the session.
I've offered to keep working for free until I could fix things, "just give me
access to your repository". He then explained that the project was actually for
some school, so he couldn't have any commits from someone else. He could not be
getting any help.

With mixed feelings of shame and anger, I helped him via chat, until I finally
remembered of <code>git revert</code>. Then, suddenly, it occurred to me what
was wrong the whole time: I had forgotten to setup the S3 region in an
environment variable. It was *that* stupid. Just that little omission gave
birth to this spiral of mistakes.  Though the error message wasn't clear, I had
had that problem before, but this time I was so immersed in the path I had
chosen that I couldn't think outside the box.

Finally, that nightmare was over. My client didn't blame me, and completely
understood that sometimes these things happen when developing software. But I
could not stop blaming myself. That day, my confidence got so shaken that I
almost gave up mentoring people. It took me some time to start taking sessions
again.

Some months have passed since then, and when I think about it, there was a
clear sequence of events that lead to this situation. Everything, from not
being able to use the remote control, neither to spend more time or money, nor
to commit directly to his repository, made me lose my sense of control. And
once that happened, my confidence started to go downhill. One mistake after
another made sure to perpetuate the feedback loop.

That said, I've learned a lot from this experience. One should:

* not be so overly confident that he doesn't even pause to really assess the
  error messages;
* question the client whether there's any constraints about the session
  (deadlines, money, privacy or access restrictions) beforehand;
* be sure to have a set of tools at his disposal that give him a sense of
  control (possibly with some backup plans);
* make small and frequent commits, just like he would do if the client's
  project was his own;
* be transparent if he's not comfortable with any constraint or lack of tools.

I wanted to write this post so that anyone could see that *it's normal* to make
mistakes. You'll make them, and even though they are just a small fraction of
your work, you'll feel much more affected by them than by your successes, but
don't let that discourage you. Make some notes, learn your lessons, and repeat
after me: "This was a valuable experience, and though it was though, it doesn't
represent who I am".
