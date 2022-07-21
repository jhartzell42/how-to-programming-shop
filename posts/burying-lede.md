+++
title = "Burying the Lede"
date = "2022-02-02"
slug = "buried-lede"
author = "Jimmy Hartzell"
tags = ["essay", "writing"]
showFullContent = false
draft = false
+++

![The Emperor Napoleon in His Study at the Tuileries - Jacques-Louis David](/images/napoleon.jpeg)

Imagine you don't know who Napoleon was. You know he's a figure from
history, but you don't even know he has to do with France. And imagine,
when you read the Wikipedia article, for some reason you skip the opening
paragraphs above the fold, and you're reading about his upbringing
in Corsica as a petty Italian noble under French rule. And you just
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

Tech writing isn't the only time this comes up, of course. The phrase
"burying the lede" is famous from journalism, the canonical example being
an article about a fire, where the article goes into details about how
it might have been started, it talks about how this is the third fire
this year, does a brief profile about the firefighter who put it out,
and then finally, at the end of the article, mentions with gravity and
somber respect, the two children who were so unfortunately lost, burnt to
a crisp.  Finally, by the end of the article, the studious reader knows
why it's the talk of the town, and the other reader, who only read the
first two paragraphs, will say something insensitive at the local pub
that night and look like quite the asshole.

For another example: I remember being a high schooler in the early aughts,
and hearing, as was often discussed then, about Halliburton. What,
exactly, was Halliburton and what do they do as a business? Democratic
Congressmen complained about them so much, but what, actually, was the
company, and what business did they have in Iraq? Literally, what were
they doing there? As in, what were they doing while they were there?

And so, a friend and I decided we'd look at the Halliburton website.
And besides an option to sign up to pay $300 to be some sort of member
of something, and a careers page that shined no light on our question,
there simply wasn't very much content to go off of. Lots of testimonials
and statements about how they were simply the best in the business -- and
clearly it had something to do with oil, though this had to be gleaned
as even that was not explicitly stated -- and nothing, absolutely nothing,
about what exactly the business was. My friend said they did "consulting"
on oil fields, but I didn't know what that meant then, and even now,
"consulting" is one of my least favorite terms on account of how vague
it is.

Of course, what we should have done is gone to Wikipedia. I don't
know what it said then, but [now](https://en.wikipedia.org/wiki/Halliburton)
it has a pretty darn helpful second sentence, opening with:

> Halliburton Company is an American multinational corporation. In 2009,
> it was the world's second largest oil field service company. It has
> operations in more than 70 countries

"Oil field service" is much more evocative and specific than anything
it said on the Halliburton website at the time (or even now). And it
also is a link, to an
[list](https://en.wikipedia.org/wiki/List_of_oilfield_service_companies)
of such companies, which doesn't explain much about them but at least
tells us the first thing:

> This is a list of oilfield service companies – notable companies that
> provide services to the petroleum exploration and production industry
> but do not typically produce petroleum.

Of course, it's still unclear what those services actually *are*. Do
they build equipment, install equipment, run trainings for the
people who actually drill it? Do they help staff the oil fields?
Lots of actual questions. But I'm a lot further ahead than I would've
been just looking at the Halliburton website. Not very much, but a
lot further.

Actually, if anyone in my readership can give me any insight on what
Halliburton actually, specifically does, please let me know in the
comments. Thank you for indulging me in this anecdote about the petty
frustrations of my youth.

Now back to the topic.

Let's look at a better, cleaner example of a lede, what
Wikipedia [actually has to say](https://en.wikipedia.org/wiki/Napoleon)
about Emperor Napoleon in the very first paragraph:

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

That's a lot to unpack, but I think it's a fairly solid intro
paragraph! For the record, I did not choose it because I knew
ahead of time that it was going to be a solid intro paragraph.
I just happened to be thinking about Napoleon when I started this
essay, and I trusted Wikipedia to provide a solid introduction to
such a historically important figure, and Wikipedia did not
disappoint.

Which is all to say, this solid quality is pretty standard on
Wikipedia. How do they do it?

It turns out they have some [pretty nice
policies](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Lead_section),
specifically about the [first sentence](https://en.wikipedia.org/wiki/Wikipedia:Manual_of_Style/Lead_section#First_sentence).

I always appreciate how Wikipedia starts out biographies by saying
the person's nationality and what jobs or activities they were
known for.  Napoleon was a French military and political leader.
[Gramsci](https://en.wikipedia.org/wiki/Antonio_Gramsci) was "an Italian
Marxist philosopher, journalist, linguist, writer, and politician."
This is especially important, because other sources are likely to
assume I know who a famous person is, especially actors and athletes,
neither of whom I'm likely to recognize the name of. You can't assume
the audience already knows Napoleon was Emperor of the French -- or that
Robin Williams was an actor -- especially if you're an encyclopedia! If
you can't learn such things reading an encyclopedia, where can you?

I also appreciate that Wikipedia explicitly highlights the level of
importance of the figure. It's not hype when Wikipedia says that Kafka
"widely regarded as one of the major figures of 20th-century literature"
or that "Napoleon dominated European and global affairs for more than
a decade while leading France against a series of coalitions in the
Napoleonic Wars"; in both cases, it's something that readers really
ought to know.

All in all, though, this comes down to having a taste for saying
the otherwise obvious. The editors who wrote these lead paragraphs
knew who Kafka and Napoleon and Gramsci were, had a lot more expertise
than the people who'd need these basic facts. But with effort, with the
aid of explicit lists and examples of other articles, they were able
to communicate to the less knowledgeable effectively.

Go and do likewise! Do likewise in your documentation. Explain to me
what your programming project does, who it's for, what its role is
within your company. In the comments/developer docs: Tell me what the
most important files are, where the main loop is, where you go to
modify various things.

And for goodness sake, tell me what problem the darn thing is
trying to solve, and what type of thing it is (e.g. program, library,
framework, specification, protocol).
