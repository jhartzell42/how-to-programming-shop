# Version Control

* Use version control for all projects

This is hopefully obvious to all modern teams, but I wanted to make sure
I said it anyway to talk some about why it's important.

The first and more obvious upshot of version control is being able
to undo and research mistakes. If the code changed how it works, developers
should be able to ask "when did it break" before asking "how did it break."
If the changes in the log are fine-grained enough, this might prevent the
need for investigating the "how." (Note that bisecting often requires
fast dev turn-around as well -- these are interconnected.) Version
control should always be used. Even informal, one-person projects, such
as writing test programs to try out APIs, should exist within a
version-controlled repo.

The second upshot is that it enables collaboration. This also makes it
important even for very small projects, because it enables you to easily
ask your colleagues for help, and your colleagues can then look at the
code with their own preferred development environment and try out fixes
on their own machine.

* Developers should be proficient in Git

It's not enough to [cargo cult](https://xkcd.com/1597/) Git knowledge
or focus on that "one guy who understands Git." Everyone should put the
effort in to be that "one guy." If you don't know what "reflog" means
or how rebasing differs from merging or how to edit commits deep in
the history, you're not a sufficiently proficient git user. Many, perhaps
even most, programmers aren't.

* Avoid mono repos

This one's simple: The git log is too spammy and CI for the whole thing
takes too long to run. Also, we have the technology of submodules, or,
if on Nix, [`nix-thunk`](https://github.com/obsidiansystems/nix-thunk).

* Do not check in commented-out lines or dead code or dependencies

It is a well-known aphorism that programmers read code more than they
write it. But more than reading it, they skim it. Let's say you
want to write new code to be compatible with old code, and you
have a simple question about the old code, like "What library
does it use for http requests? We need to be compatible with that."
You might look into the deps, see `libcurl`, then look into
the C file, and see:

```
#include <libcurl.h>
```

And then you might skim down and see a bunch of related calls, and then
say, alright, we need to be compatible with `libcurl`. But, it may
turn out that that dependency and those lines haven't been used
in aeons, that every single call is commented out, and someone just
left the resulting code in. The person was misled.

If you're removing code, do it. If you're worried about being
able to change it back, well, that's what version control's for.
If you really want to, you can make a comment that said it used
to work differently, and even say what known-good revision used
the other system.

But instead of commenting out code, delete it. If there's a function
you now no longer call, remove it. If there's a dependency you no
longer use, drop it. Otherwise, it will only confuse future readers.
