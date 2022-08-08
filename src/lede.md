# The Lede

* Documentation should have a lede paragraph that states the "obvious"
things.

Let me explain:

Imagine you don't know who Napoleon was. You know he's a figure from
history, but you don't even know he has to do with France. And imagine,
when you read the Wikipedia article, for some reason you skip the opening
paragraphs above the fold, and you're reading about his upbringing
on Corsica as a petty Italian noble under French rule. And you just
want to know, why's this guy important, what's his deal, why do people
keep talking about him (something military, it seems?)  but you have
to read two-thirds of the way through the article to find out, oh, he
became *Emperor of the French*. Finally, you have context to understand
everything else, and you now know the first thing about Napoleon.

This is how I feel reading technical documentation, not all the time,
but a fair amount of the time. I hear about a new project, and I get
documentation about it, and it immediately goes into the weeds.
What is a Foo? Is it a library, an application, a command-line utility?
It's a "framework" -- that word means several things, but I'm guessing
it means it's a library that dictates how an application is written?
Who would use this framework? What problems does it solve for them?
Oh, I see it uses a bunch of technologies to solve the problem,
but what problem is it trying to solve, exactly?

For example, you often see documentation that *just* has build
instructions, or a list of what each API method does.
Oftentimes, you will see documentation for a protocol just launch
into the wire format:

> Each SXP message contains a 4 byte ID number in network byte order,
> and then a single byte indicating message type.
>
> There are 19 message types, each listed below, distinguished
> by their first bytes:
> * **0x01** Go-ahead messages
> These contain no content.
> * **0x02** Cancel messages:
> These contain 4 bytes, indicating the message ID being cancelled.
> ...


If I'm supposed to be implementing one side of this protocol, or interacting
with it in any way, I still have a number of very basic questions. What
do these messages actually do? In fact, what does this protocol, in general,
do? Why do we have it? So much of programming is moving data around from
one place to another in different formats, and I get that a lot of it is
for historical reasons, but could you at least tell me which data is
being moved between which places?

## Reasons for Lede-Burying

I understand why documentation is written like this. I understand why
it skips over basic questions. It comes from a few different places:

1. We are trained to not state the obvious.

Documentation is very different from normal human interaction. In normal
human interaction, there is a high premium on not stating the obvious --
it's insulting. At the same time, in human interaction, there's little
cost if we overdo it and the listener does have a question we think of
as obvious -- the listener can just ask it.

If someone asks me, "tell me about your kitchen," it would be a waste of
time and kind of weird to earnestly start out with "Well, it's where
I cook all my food." Similarly, an expert historian asked to say some
things about Napoleon might think it'll be taken as condescending if they
say the basic things about him that are supposed to be common knowledge.

This habit is implicit and automatic and very unnatural for most people
to break. And it simply doesn't apply to documentation. In documentation,
people understand and can skim intro paragraphs and won't be offended by
reiteration of the basics. In documentation, people can't ask questions
because the document's already written. But habits from conversation
spill over into documentation-writing.

And of course, what we find obvious after working on a project for
months is exactly what the new-comer needs to know first.

2. We aren't even consciously thinking about what we find obvious.

If you ask a historian to name some facts about Napoleon, the fact
that he was Emperor of the French probably won't come to mind. The
historian doesn't think about Napoleon being Emperor of the French
explicitly at all.

Instead, it's in the background of all the other facts. When the
historian thinks about Napoleon growing up on Corsica, he's thinking
about how ironic it is that Napoleon probably grew up speaking Italian,
given his future position as French Emperor. When he says this fact
as the first thing he mentions about Napoleon's life, he thinks you're
thinking the same thing.

Similarly, if you've been working on a project for years, the basics
fade into the background of your mind. They're the context behind
the thoughts, not the conscious thoughts themselves. This is why
documentation writers don't include them, but also why it's so fundamental
to include them.

3. People write documentation implicitly for themselves and for the in-group.

If a historian is writing for other historians, they don't need to tell
them that Napoleon was Emperor of the French. They certainly don't need
to say that when taking their own notes.

Oftentimes, documentation grows out of developers writing notes to themselves
or to each other while the project is being worked on. The basic, obvious
stuff is irrelevant to that.

## How to write a lede, then?

In journalism, they use the "5 'W's": *who*, *what*, *when*, *where*,
and *why*, to help them remember to say the obvious thing. In programming,
we need our own system.

In programming, the biggest question isn't "who" and "what." Technical
documentation comes with different "w"s.

1. What category of thing is it?

This one comes first because it's the most obvious, and therefore the
most important as background context, the most necessary to understand
everything else. If you're talking about a protocol, and the other
person thinks you're talking about an application, that's going to lead
to some confusion.

The first thing the actual Wikipedia article says about Napoleon, after
listing the many forms of his name, is that he was "a French military
and political leader." You might not realize that from seeing that he
grew up on Corsica. Strictly speaking, you could potentially mention that
he's a human beforehand, but that might actually be too obvious even
for a lede paragraph, or perhaps just implied by "French."

You would not imagine how confusing this can be if you don't do this.
I've sometimes heard a famous person discussed in detail, and not
known if they were a musician or a politician (they turned out to be
a comedian). I've often heard people drop acronyms, and assumed they
represented pieces of software maintained outside the company, when they
turned out to represent protocols, or software maintained inside the
company, or even common communication problems.

So let's start to write our new lede paragraph for this protocol:

> SXP is a protocol.

Now that we remembered to mention that `SXP` is a protocol, we might
remember a bunch of other information that goes with it. That's a good
thing, and you should probably write it down, but it doesn't necessarily
go in the lede paragraph, or at least not in this position:

> SXP is a protocol that can either use TCP or UDP. TCP connectivity
> must be enabled by a prior UDP-based handshake between the peers,
> which can be configured by...

Perhaps one adjective or two is appropriate, because the lede paragraph
has other questions to answer:

> SXP is an IP-based protocol.

Note that we can and should be specific without being side-tracked.
We can say "process" or "set of processes" rather than "application."

Great! Next question!

2. What problem is it trying to solve?

If I need a tool for a project, and I'm reading the manual, I probably
already know what the tool is for. But if I'm maintaining a codebase,
But technical documentation isn't just for the users; it's for the
maintainers. I might just have been told by my boss to fix something in
there, or just to familiarize myself with it because it's going to come
up in a future project. It's not necessarily obvious what it's for.

And maintainers really need to know what something is for. If we don't
know what problem we're trying to solve, how do we know if we're doing
a good job at it? How can we make it do a better job?

So this comes next: Why does this protocol or application exist? What
problem is it trying to solve? This goes at all levels, not just the
top level of documentation. Our example bad documentation leaves
this question unanswered at many levels; not only does the document
lack a lede, but each subsection needs a bit of context as well:

* What problem is the protocol trying to solve?
* What problem is the go-ahead message trying to solve?
* What problem is the ID field trying to solve?

3. What is its position within the greater system?

This is connected in practice to what problem it's trying to solve.

* Who uses it?
* Is it user-facing, or internal?
* Server-side or client-side?

4. What technologies is it layered on top of?

* What programming language is it written in?
* What platform is it supposed to run on?

This is where we can start writing about UDP and TCP.

## Other Examples of Lede Paragraphs

> This is the main repo for our flagship product, and it is one of
> our few repos that is not open source.
> Customers use it directly to control the widget machines, which it
> contains all the drivers for, and also Node.js code to serve
> the user-facing web interface.

> This is run as a twice-daily batch job to automate pruning the
> widget description files. It is run on customer machines, and is
> open source as local administrators might want to customize it.
> It is written entirely in Perl 4 except for one module that is
> written in APL. Sometimes, it doesn't work correctly, and we have
> to manually run an earlier version written in JCL and Cobol (link).

> This implements the new DSL for widget description. Currently, it only
> supports translation to old widget descriptions, but it is hoped that
> it will eventually be integrated into the main repo. It is a research
> project still under active development. It is written in Haskell
> and Idris, and contains, as a component, a custom Prolog interpreter.

And, of course, the actual Wikipedia lede about Napoleon, which is quite
good and which our hypothetical reader shouldn't have skipped over:

> Napoleon Bonaparte (born Napoleone di Buonaparte; 15 August 1769 – 5 May
> 1821) was a French military and political leader who rose to prominence
> during the French Revolution and led several successful campaigns during
> the Revolutionary Wars. He was the de facto leader of the French Republic
> as First Consul from 1799 to 1804. As Napoleon I, he was Emperor of
> the French from 1804 until 1814 and again in 1815. Napoleon dominated
> European and global affairs for more than a decade while leading France
> against a series of coalitions in the Napoleonic Wars. He won most of
> these wars and the vast majority of his battles, building a large empire
> that ruled over continental Europe before its final collapse in 1815. He
> was one of the greatest military commanders in history, and his wars
> and campaigns are studied in military schools worldwide. Napoleon's
> political and cultural legacy has endured, and he has been one of the
> most celebrated and controversial leaders in world history.
