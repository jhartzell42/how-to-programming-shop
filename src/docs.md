# Documentation


* Documentation should say how to build the project

It should, as mentioned, be one command, and it should not depend on very much
set up beyond "having a standard development workstation."

* Documentation should say how to run the project

What flags or configuration does it take? How do you tell it to re-read
the configuration? Does it use any environment variables?

* Documentation should say what the project [is for](/posts/buried-lede)

This should be before how to build it and run it, and should
explain who might want to run it and where it fits into the broader
organization, and the first things a programmer might want to know
before looking at it. This will help people understand the stakes
of modifying it, and where to start looking for features. This
should be covered in the lede paragraph.

Which leads me to:

* There should be a lede paragraph

This should introduce the repo to someone who's never heard of it
and doesn't have any context for what they've stumbled across. It should
include its role in the company's tech stack, its status, and what
technologies it uses.

Here's some examples:

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

* Documentation should be discoverable

It should either be in the `README.md` of the relevant repo or linked
to directly from there.
