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
