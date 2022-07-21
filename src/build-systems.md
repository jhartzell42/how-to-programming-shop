# Build System

You've changed a line of code. Congratulations! Now how long will it be
until you can see the results of your change in action? How many steps
do you have to take to see if it fixed your issue? If it broke compilation?
If it passes tests?

If the amount of time or number of steps is low, then people will be able
to try out various solutions, use trace statements to debug issues, and
otherwise interact with their code like a live system. If it's high,
they have to rely more on their own reasoning, which is fallible, more
likely to lead to bugs, and more likely to lead to timid, overly-conservative
changes, that work around problems rather than addressing them.

So how do we accomplish this?

* Projects should run natively and directly on developer workstations

In my mind, this is almost a deal-breaker for development. If you have
to deploy to a dev environment or install on a physical piece of embedded
hardware to test your software, your dev cycle will be far too long. Dev
environments and physical hardware are of course essential for testing,
but using them for absolutely all development introduces resource
constraints where there don't have to be, and lengthens dev cycles.

Even if the local dev environment is different from the prod environment,
that's fine. Even if some of the code won't run and make sense, it's still
important to be able to run the rest of code locally. Even if it's running
on an embedded platform and operating system with no proper simulator,
some of the code will work on Linux or macOS. Those components should
be testable on the developer workstation itself.

* Building a project locally should be a single command
* Building and running automated tests for a project should be a single command

When I say a single command, I mean it. Exactly one. Two is far too
many. Once you try it, you'll never go back. If your workplace doesn't do
this, write a script. Check the script in.

Of course, if different developers have different computers, this
might be difficult, but if you assume a standard set of dependencies,
(or use a reproducible build system like NixOS), this command can
just be an invocation of the build system.

In situations where it's more complicated, a shell script should be
written to encapsulate the complexity. This shell script should be included
in the repo and maintained and checked by CI along with the other code,
so that it always works. The exact invocation of the command should
be completely invariate, and documented in the projects `README.md` file.

Programmers don't need to be distracted by complicated multi-part
instructions that haven't worked exactly right in years, or that work
on some machines and not others or by twiddling with their Docker
settings. They should be focused on actually improving and fixing
code.

* Building and running a project locally should be a single command

This is similar to the above but might require sample configuration to
be checked in along with the repo.

* Builds should be reasonably fast

Developers should program on sufficiently powerful computers for their
builds. Build scripts should use options like `-j` and if helpful send
builds seamlessly to build farms (the seamlessness is important; it
should still be a single command for the developer and result in a local
build and run). Private caches should be set up, if this is possible
with your build system.

If programming in C or C++, header file hygiene can be
an important consideration in build speeds -- invest time into it.
Use incrementality features of your build systems rather than having
scripts that clean every time. Structure the code so that incremental
builds are possible.

If necessary, allow developers to build only part of the project (while
still making it simple to build the entire project).
