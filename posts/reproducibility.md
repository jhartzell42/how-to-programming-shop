+++
title = "Can you reproduce it?"
date = "2022-03-22"
slug = "reproducibility"
author = "Jimmy Hartzell"
tags = ["essay", "computers", "programming"]
showFullContent = false
draft = false
+++

*NOTE: This post has the #programming tag, but is intended to be comprehensible
by everyone, programmer or not. In fact, I hope some non-programmers
read it, as my goal with this post is to explain some of what it means
to be a programmer to non-programmers.*

What is the most important skill for a software engineer?  It's
definitely not any particular programming language; they [come and
go](https://www.biblegateway.com/passage/?search=Ecclesiastes%201%3A4&version=KJV),
and a good programmer can pick them up as they work. It's not estimating
how long a project will take, as important and elusive as that skill
is -- because fundamentally, no one can, and many, many programmers are
successful without having fully built up that skill.

No, in my learned and considered opinion, the most important skill in
a software engineer is solving -- and preventing! -- problems. It is
squashing and preventing "bugs" -- those situations where the software
behaves in an undesirable fashion, where it fails to meet expectations,
whether or not you knew about those expectations ahead of time. That
is the crux of the software engineering skillset. Preventing and fixing
bugs is the goal which the other skills uphold, and the criterion by
which software engineering principles and practices should be evaluated.

My other programming posts can be understood through that lens. All my
posts on why Rust is a better programming language than C++ -- the point
is that Rust, as a programming language, is top-notch bug repellant
technology. For any post about code organization and readability, the
reason it's important for code to be organized and readable is so that
another programmer trying to find a bug is able to find it quickly,
or that a programmer trying to add a feature doesn't end up also adding
more bugs, due to a misunderstanding of how the code works.

But today, I wanted to talk less about the prevention, and more
about the squashing, about what to do when you've found a bug.

So how do you squash bugs?

First, I want to note that the most important bug-squashing tool is the
human brain.

There is a tool, a type of program, called a "debugger," but that is
less essential than you might think from the name. A debugger won't fix
bugs for you, and unless the bug is a crash that actually happened, it
can't even find them.  If a debugger could fix -- or even just find --
all your bugs, that would be almost equivalent to a program that could
write programs, because, as mentioned before, preventing, finding, and
fixing bugs is the crux of the entire job, and I know it hasn't been
automated, because I still get a paycheck.

What a debugger *can* do is attach to a running program, let you run it one
line at a time instead of all at once, and let you inspect the program's
internal state to make sure it is what you think it is. Additionally,
if there is a crash, the debugger can inspect the crash data, sometimes
in the form of what's known as a "core dump," and tell you what line
of code was running when the crash happened, a "backtrace" of how the
program got there, and what values were in what variables then.

This is all useful in the debugging process, but not essential.  The
program ought to be called an "inspector" -- or perhaps the "debugger's
companion," because as a programmer, the true debugger is you, and much
of what the "debugger" tool can do, you can do without it as well, using
(for example) more verbose log lines and error messages, and just good
old-fashioned reasoning power.

So what do you do, when you have a bug? Where do you start?

You might assume that the first thing to do when you see a bug is to try
to find out what caused it. But not only is that going to be difficult
without some initial steps, it can lead to problems, where you think
you've got it, you go and do your fix, think it's better, and actually
the bug turns out to still be there.

No, more important than trying to guess what might have caused a bug is
figuring out how to tell when the bug is actually fixed. If all we know is
"sometimes, the app crashes," and we change something, and the app doesn't
crash right away, well, is that because we fixed it, or is that because
it just happened to be one of those times where the app doesn't crash?
If I had a nickel for every time a programmer *thought* they'd fixed
a bug...

And this is where, although programming [definitely
is](https://www.hillelwayne.com/post/are-we-really-engineers/) a type of
engineering -- software engineering -- it has an advantage over other
engineering fields. With software, we can run the same program over
and over again, often almost for free, in a way that we can't rebuild
a bridge or dig a new mine tunnel. With software, often -- not always,
but usually -- we can re-run a program, do a few things, and see if the
bug arises again. And then, through experimentation, we can come up with a
procedure that allows us to *always* trigger the bug.

In this way, "sometimes the app crashes" can be refined through experiment to
"when you go to the settings page in particular, sometimes, the app
crashes" which can then be refined to "when you go to the settings page,
and you're not logged in, and you're on an iPhone from the past 3 years,
it crashes *every time*." And now, you have a way of knowing when you've
fixed it. If you do those exact things, and it doesn't crash, then you can
be confident that your fix actually took.

Refining the conditions in which your bug is a bug, or rather, coming
up with a list of instructions to make the bug happen on purpose --
ideally as short a list as possible -- is known in the business as
"reproducing the bug." And it is the most important skill-set in
people who are testing software.

Because if I've written some code, and someone else is testing it,
and they've gotten it to crash, but don't know how or why it crashed
-- or especially if they don't even know what they were doing when it
crashed -- well, that doesn't do very much for me. I have no idea where
to even start. Because I haven't experienced any crashes, I can't
look at your crashes. It works on my machine. How can I solve a problem
I can't even see?

So this was a problem for me when I was a lowly iPhone programmer working
in a small three-person company. My app would have error messages pop
up -- and this was frequent, as my boss, who was not a programmer,
didn't let me spend time improving how the app worked unless I was
making continuous visible progress. My boss would tell me that he'd
gotten an error message while using the app. Can I look into that?

I didn't know what to do. I always looked into it when I got error
messages, and was often able to reproduce them, find them, and fix them,
but obviously my boss was better at QAing my app than I was --
at least in the triggering bugs department. So I told him so. "I don't
know what to do -- I can't fix it unless you can reproduce it."

What happened subsequently confused me. My boss would text me, giddy,
for some reason acting as if he was winning an argument against me,
saying "I reproduced it." And then he'd send me a screenshot of the
problem. He did this repeatedly. He seemed to think "reproducing the
bug" meant screenshotting the bug in action.

Later I saw him in person, and he asked me about whether I'd fixed the
bug yet.  I tried to explain that that wasn't enough; what I needed was
a step by step explanation of how to make the bug happen.  And he said
something along the lines of, "How can you still not believe me? I sent
the screenshot."

I was flabbergasted. I said, "Wait. I'm not literally doing this as
a policy, where I don't work on it unless you prove to me there's an
actual problem. It's not because I don't believe you.  It's not because
you have to convince me it's real before I work on it."

And my boss responded, with an affected, over-the-top laugh, "Haha,
no I get it." And then paused a second and continued, "But you kinda
are though. That's exactly what you're doing."

Apparently, when I said "I can't," my boss heard "I won't." My boss
thought this was about me standing up for myself against potential
spurious work, and being overly strict about burdens of proof, rather
than me literally asking questions that would make it possible for me
to do my job and troubleshoot these issues.

At this point, I was just shocked. How did he think I was going to
do my job?  Obviously I have to figure out what was going wrong. And
obviously -- or at least it was obvious to me -- that required follow-up
questions. Why was he so affronted by my follow-up questions? What
did he think fixing the issue looked like? Did he think I'd just say,
"Oh, error messages.  I must have left some extras in. I'll go take them
out." No, the error messages were the visible result that happened when
the code didn't know how to proceed to accomplish its tasks, and I had
to go deeper in to find out why that was happening.

Luckily, I was able to compose myself, and think quickly on my feet. I
knew I wasn't going to be able to actually explain reproducibility
to him -- after all, I just had, and he somehow misinterpreted it as
insubordination -- so I fibbed a little.

The debugger that came with Macs for debugging iPhones looked very
sophisticated, and to use it with the app, you had to connect the phone to
the computer with a cable. This would allow you to, as I said before,
inspect the current program state, and so on. It looked like a very
useful tool -- and it was. Just not as useful as the human brain,
and not something you could use to skip steps.

But even though what I really needed was instructions on how to make
the bug happen, I told my boss that what I needed was for the bug
to actually happen *while* the phone was plugged into the debugger.

This served two purposes: It made him believe me that I wasn't just
messing with him, and it gave him a concrete reason to reproduce
the bug. Now that he had the goal of making the error message pop
up while it's plugged in, he was able to figure out for himself
that the easiest way to do that was to come up with a way to make
it happen on purpose.

Now, when he found a new bug, he wouldn't bring it to me until he was
prepared to make it happen while it was plugged in. Some of them, he
already knew how to trigger; he just hadn't heard an adequate explanation
for why he should tell me. Other bugs, he would figure out. In either
case, once he was done, he would make the bug happen while it was
plugged in.

And when this happened, I could either ask him how he got it to happen,
casually, while pretending that the more important thing is that it's
plugged in, and while he sees that I'm using a computer and therefore
"working" -- or, if the steps were inconsistent or unclear, or if we'd
just gotten lucky to see an error message while attached to the debugger,
I could use information from the debugger to figure out what the program
had been doing before the error -- and use this, not to fix the bug
immediately, but to figure out how to reproduce it myself.

So what did I learn from this experience? Well, even though the most
important tool in programming (and bug-squashing) is the human brain,
I learned that people, especially non-programmers, are more comfortable
when they see you using other, concrete, fancy-looking tools. And if
your human brain needs input to complete a task, people might be more
likely to give it to you if you pretend the computer needs that input.

For those of us who work primarily with our brains, this can be
frustrating and disappointing, and can lead to the need to fib a little
sometimes to accommodate these biases.

And additionally, I learned about the depths of the disconnect between
different levels of expertise. I thought it was obvious that to fix a
problem with some code, you had to understand it at least well enough
to make it happen again. This seemed to follow directly from first
principles, to be the only logical way that it could work, if you thought
about it. But my boss hadn't thought about it, and didn't understand
this. The gap in our perspective didn't come from his lack of detailed
technical knowledge or specific technologies, but rather from his lack
of a developed intuition for how programming works.
