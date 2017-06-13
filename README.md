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
1. After a second commit
    ```
    jpollak at Veterok in ~/src/git-tests (master)
    $ git describe
    v1.0.0-1-g9ded7c3
    ```
1. Added branch `forka`
1. Added branch `forkb`
1. After commit on branch forkb:
    ```
    jpollak at Veterok in ~/src/git-tests (fork2)
    $ git describe --tags
    v1.0.0-2-g88520c3
    ```
1. Another commit on forka
    ```
    jpollak at Veterok in ~/src/git-tests (forka)
    $ git describe --tags --abbrev=0
    v1.0.0
    ```
    As expected
1. To get the sha of a tag:
    ```
    jpollak at Veterok in ~/src/git-tests (forka)
    $ git rev-list -n 1 v1.0.1
    b812b64072834cc8e883cb7e57ab6804c97b724c
    ```
1. Added More commits
1. Tag _previous commit_
1. After merging forkb into forka:
    ```
    jpollak at Veterok in ~/src/git-tests (forka●●)(merge)
    $ git describe --tags --abbrev=0
    v1.0.1
    ```
    So that is good...
1. 28 days later, more work
1. Trying to add more to forka
1. This is feature/forkc
1. This is another commit to feature/forkc
