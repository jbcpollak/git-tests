This document is a log of the behavior of `git describe` in various states of a git repository, for my own understanding:

1. Immediately after `git init`, with no added files or commits
    ```
    jpollak at Veterok in ~/src/git-tests (master●)
    $ git describe
    fatal: No names found, cannot describe anything.
    ```
1. After committing README.md for the first time:
    ```
    jpollak at Veterok in ~/src/git-tests (master)
    $ git log
    commit e7a3154c3fcd28dd4603a2badf22f6b717b270b7
    Author: Joshua Chaitin-Pollak <josh@offthehill.org>
    Date:   Mon May 15 10:31:35 2017 -0400

        initial commit

    jpollak at Veterok in ~/src/git-tests (master)
    $ git describe
    fatal: No names found, cannot describe anything.
    ```
1. After `git tag v1.0.0`
    ```
    jpollak at Veterok in ~/src/git-tests (master)
    $ git describe
    v1.0.0
    ```
1. Added branch `fork2`
1. After commit on branch fork2:
    ```
    jpollak at Veterok in ~/src/git-tests (fork2)
    $ git describe --tags
    v1.0.0-2-g88520c3
    ```
1. Added More commits
1. Tag _previous commit_
1. Trying to do a semantic-release version calc - I'm expecting v1.0.2-forka1
