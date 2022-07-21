# CI

Before code can be merged into master, it should build. By default, merging
into master should be impossible unless the repository has verified the
build with CI. This is where we can easily test that it builds in a
deployment setting in addition to a development setting, where
artifacts can be created to deploy to servers or embedded devices
(though this should also be possible to do locally) and where
we can run automated tests. Coding standards should be enforced here,
through lints. `clippy` and `cargo fix` are great tools for Rust.

Ideally, your CI scripts should be checked into the same repo as the systems
they test, as is supported by GitLab with its `.gitlab-ci.yml` files.
