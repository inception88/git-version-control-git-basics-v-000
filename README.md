# Git Basics

## Learning Goals

- Identify how to initialize a Git repository with `git init`
- Check the status of a repository with `git status`
- Keep track of file changes with `git add`
- Create a commit and apply a commit message with `git commit`

## Introduction

In our overview of version control systems, we saw that using a VCS helps us
organize our work and keep track of changes we make. We also determined that the
VCS we're going to use is Git. Now we can begin learning the commands we need to
make Git work for us.

## Identify How to Initialize a Git Repository with `git init`

Git operates on a directory level. When we have a new directory that we want to
track our files in, we need to _initialize_ the directory as a Git repository.
That means Git will then pay attention to what goes on in the directory and give
us all the Git superpowers.

To get started, we'll create a new directory. Go to the terminal and type the following:

**REMEMBER** Don't type the `$`. That's the universal symbol for a command prompt.
It's how technical documentation says "Here's a thing for the shell to process."

```
~ $ mkdir my-git-project
```

This command creates new directory. Then:

```
~ $ cd my-git-project
```

This command moves into the newly created directory.

Now that we're in the directory where we want Git to watch for changes (adding,
removing, and editing files), let's set up this directory by _initializing_ it.
In the terminal type `git init`. It should look like this:

```
my-git-project $ git init
Initialized empty Git repository in /Users/avi/my-git-project/.git/
```

Git lets us know that it has put `/Users/avi/my-git-project` under its protection.
Git also tells us that it stores its own data in the `.git` directory. This hidden
directory, `.git`, is what Git uses to keep important stuff, like the commit
history. Don't go in there and start randomly deleting things! That said, if ever
you do `git init` in the wrong directory, you can `rm -rf .git` and return the
directory to a plain-old, unprotected directory.

> Be careful about making an entire directory, like our home directory or our
> desktop, into a Git repository accidentally. Make sure you only type `git init`
> _within_ the directory you want `git` to track.

## Check the Status of a Repository with `git status`

Now we have Git watching this directory, let's see what it can tell us about the
directory. The command we use for this is `git status`.

```
my-git-project $ git status
```

Since we have not added any files yet, we'll see:

```
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
```

Let's create a `README.md` that describes the project. Make our new file by
typing `touch README.md` from within the `my-git-project` directory. We won't
see any output after `touch`, but we will see a new file has been created if we
type `ls` (which gives a list of all the files in the directory).

```
my-git-project $ touch README.md
my-git-project $ ls
README.md
```

With at least one new project file we can enable Git to start tracking changes.
Type `git status`. Git will show us what our current repository looks like and
what changes it sees.

```
my-git-project $ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

  README.md

nothing added to commit but untracked files present (use `git add` to track)
```

Git confirms that it's aware of the file `README.md`, but it's not "tracking" it.
Git's not doing anything with the file and the file is not doing anything with
Git..._yet_. Let's change that!

> **IMPORTANT**: Whenever we want to check the status of our Git repository &mdash; which we do
often &mdash; type `git status`.

## Keep Track of File Changes with `git add`

Currently, the file in our repository is not being tracked by Git. We
have to tell Git about all the files we want it to keep track of and consider as
part of our project. We can do this by _adding_ the files to our `git` repository
with `git add <filename or path>`. To add our new `README.md` to the repository
and check the status, we type:

```
my-git-project $ git add README.md
my-git-project $ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

  new file:   README.md
```

We can now see that Git is ready to keep track of `README.md`. All the changes
in the file at the time we `added` it are "staged." If we were to change `README.md`,
we'd need to re-add the file. As it happens here, this staged change is "create the
file, nothing inside of it" because `touch` created an empty file.

To save a new _version_ of this new file (or, later, to "capture" changes
to a file) we need to _commit_ the set of changes or "diff." We "save" the changes
in our repository by making _commits_.

## Create a Commit and Apply a Commit Message with `git commit`

Remember: `git add` got our changes to the repository ready in the previous step. Those
changes are the ones that will be "captured" with our commit.

To make our first commit, type: `git commit -m "Initial commit"`.

This tells `git` that our commit message, represented by the `-m` flag, is `"Initial commit"`.

```
my-git-project $ git commit -m "Initial commit"
[master (root-commit) e55477d] Initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
```

We can see that Git has created a new version of our repo, represented by the
_SHA_ `e55477d`. SHAs are the identification system that `git` uses to keep track
of versions; they're long complex numbers and letters that are unlikely to be
duplicated.

The `commit` command committed 1 file.

Now, if we type `git status`, we'll see
that it is at a "clean state", and there is nothing to commit and no new changes.

```
my-git-project $ git status
On branch master
nothing to commit, working directory clean
```

If we make another change, for example, to README.md, we can add another commit
with this new set of changes with 

```
git commit -am "A Message"`
```

The `-a` flag refers to adding 'all changes' on all tracked files and `-m`
specifies a commit message of `"Updates README.md"`. To review some of your
Unix CLI skills, this could also be written as: `git commit -a -m "Updates README.md"`

The commit would look like:

```
my-git-project $ git commit -am "Updates README.md"
[master (root-commit) e55477d] Updates README.md
 1 file changed, 4 insertions(+), 0 deletions(2)
```

Good work! Commits are amazingly powerful in Git. They are the heart of many of Git's advanced
features. Understanding the basic workflow of Git initialization and setup
is the foundation for success.


## Conclusion

To make a new Git repository out of a directory &mdash; which we'll only have to do once
per project &mdash; use `git init`. Whenever you make a change to a file or create a
new file, you can check the status of these changes with `git status`. When
you're ready to preserve changes, you can `git add` the files (or directories of files) with the
`git add <filename or path>` command.

Once your changes have been added, or "staged," use `git commit -m` to commit them
with a explanatory message. You can shorten the `add` + `commit` process, provided
that all the files are being tracked by using `git commit -am "A Message"`.

If we've followed all these steps, our `my-git-project` directory is now a `git`
repository. We can retain the directory as a sandbox for Git experimentation.

## Resources

- [Git Basics at git-scm.com](https://git-scm.com/book/en/v1/Git-Basics)


