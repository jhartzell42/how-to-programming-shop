# Branching Models

* Use and Enforce a Branching Discipline 

Even on relatively small projects, no one should be committing and pushing
directly to the `trunk`/`main`/`master` branch. If people push directly
to `master`, every commit is automatically collaborative. This will make
developers commit less frequently than they otherwise should, and will
decrease the effectiveness of version control by having fewer versions
to go back to.

It will also, obviously, lead to people accidentally "breaking the build"
as projects get bigger. Committing a small change and merging that
change into `trunk` or `develop` should be two different actions. The
first should be done extremely often, and the second should only be
allowed if a certain number of hoops have been jumped through.
