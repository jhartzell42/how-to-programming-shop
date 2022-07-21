# Code Review

* Require code review

This should be enforced by your Git system.


The main point of code review is not to make sure bugs don't get into
the code, although it helps with that. The main point of code review is
to mitigate [bus factor](https://en.wikipedia.org/wiki/Bus_factor), that
is, to make sure there's more than one person who is ready to maintain
the code. All other guidance flows from here.

* At least the person who maintains the code should also review

If the MR is written by the primary maintainer of the codebase,
it should reviewed by whoever would have to step up if they
were abruptly "hit by a bus."

This ensures that everyone maintaining the code is in agreement
with not just style and correctness concerns, but in the general
design, architecture, and organization of the code.

* The standard should be "Would I take responsibility to maintain this?"

If the answer is no, why not? Asking myself this question motivates me
to make more suggestions about how the code should be factored, so I
can jump in and make changes easily like I can with my own codebases,
rather than just simply verify that it looks like it works and doesn't
have any `unwrap()` calls.

This question leads to some natural sub-questions:

* How hard is it to find bugs in?

It shouldn't just not have bugs, it should be obvious it doesn't
have bugs. This way, when a bug is actually discovered, code that isn't
buggy but is complicated won't distract the poor developer trying to find
the cause.

* How hard is it to modify to do something else?
* How easy is it to mess up?

This is where DRY (don't repeat yourself) comes in. If I repeat
the same pattern of code more than 2 times, and someone modifies it, they
might only modify some of the instances of the pattern. This can
also be mitigated not through abstraction but by putting all the instances
next to each other, which is sometimes appropriate.

The code, however, should also not do premature abstraction, because
then it will be impossible to find issues among all the spaghetti of
function calls and variable references, so this is a balancing act.

* If a bug is found to be caused by this change, will we know which
part to revert?

Remember, programmers should be able to
[bisect](https://git-scm.com/docs/git-bisect) instead of having to read
an entire codebase when they want to find a bug. If you found out that
the bug was caused by this change set, would you be relieved to know or would
you still have a lot of work ahead of you?
