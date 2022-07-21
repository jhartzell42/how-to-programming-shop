# Introduction

I have worked on a lot of programming projects in my time, and while I
was a programming consultant I have worked in a lot of different corporate
environments. At some of them, it was easy to be concretely productive:
I was able to contribute immediately, and at a rapid rate. At others,
actual useful contributions would be impossible until I had a month or
more of experience with a codebase, and even then every change would be
a long slog. The difference can be overwhelming and palpable.

The biggest contributors to this difference wasn't what programming
language was chosen (though I do care a lot about
that), nor how well the code was factored (though that's also very
important), but rather the organizational structure that surrounded
the code: the build system, the repo configuration, the tests, the
documentation, the ticketing system -- the stuff outside of the code
itself that was essential to how programmers interacted with the code.
Most, but not quite all, of what I'm talking about falls under the header
of [Dev Ops](https://en.wikipedia.org/wiki/DevOps).

After having read (some of) [*Code That Fits in Your
Head*](https://www.amazon.com/Code-That-Fits-Your-Head/dp/0137464401/), I
came to believe in the importance of check-lists. This documented started
as an attempt to share with you my personal check-list of important
dev-ops and dev-ops-adjacent considerations when setting up a new project,
so that developers can work rapidly, effectively, and with fewer mistakes.
It still mostly takes the form of a check-list, of bullet-points you can
make sure you're doing, followed by explanations of why and other discussion.

The stakes are high -- if it takes forever to make a change, if the
process between modifying your code and running your code is too long,
programmers won't be able to work unless they're much more confident,
biasing them towards overly simple fixes and against more complicated
refactors. If there's no tests, programmers will be overly careful
modifying the code to avoid breaking things, and so the code won't
be able to evolve. New team members will take much longer to gear up,
and everyone will be much less productive.

The worst thing is, managers are liable to dismiss developers' complaints,
and developers are unlikely to have the confidence to raise them. It's
easy to be unsympathetic to the complaint that a job is tedious or
inconvenient. It sounds to many programmers and managers alike like
laziness, and the obvious answer is "Well, that's why we pay you the
big bucks." Obviously development at these shops is still possible,
and the old hands at the company, who are used to whatever system's in
place, have accepted the costs already.

But make no mistake: Developer convenience and happiness is closely
connected to developer productivity and accuracy. So let's discuss
how to make a development environment convenient for a developer.

So here's how we can make programming convenient. Many of these guidelines
I express here in bullet point form, and many of the themes that underlie
them and tie them together, I learned from colleagues and leaders along
the way in my programming career. This is my first attempt to collect
all of them.

Remember, paying attention to these things is a bigger multiplier on developer
productivity than finding "10x developers," and is essential for
attracting and retaining good developers. Improving these things is hard,
especially at organizations that are set in their ways, but it is
far more important than it might look. Dedicated dev-ops professionals
are essential in such things.
