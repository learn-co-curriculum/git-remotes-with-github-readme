# Git Remotes + GitHub

## Problem Statement

As strange as it may seem, GitHub does nothing special in the `git` universe.
It's just another `git` repository just like `git init` makes. The only
different thing is that it lives on a server across the internet.

A repository that's non-local is called a _remote_. You've seen how valuable
_remotes_ are for _getting_ software. Let's learn about the other side of the
equation: let's learn to mirror our _local_ repository to a _remote_ repository
using `git push` and `git remote`.

Once your code is on a _remote_, it's backed up &mdash; which is always a good
thing &mdash; and it's available for _someone else_ to `fork` or `clone` and
benefit from. Let's learn how to `push` our code!

## Objectives

1. Explain creating a remote repository on GitHub
2. Demonstrate connecting your local repository of files to your remote repository
3. Use `git remote` to set the destination of your repo
4. Use `git push` to send code to the remote repo


## Explain Creating a Remote Repository on GitHub

1. To create a new _remote_ repository, go to: [github.com/new](https://github.com/new),
while logged into GitHub.
2. Enter a name for your repository in the `Repository name` field. You can
name it whatever you'd like; be creative! The default options are fine as-is —
don't initialize the new repository with a README or add a `.gitignore` or
license. Click the green `Create repository` button.
3. After you create the _remote_ repository, you should see a "Quick setup" page. Click the
"Copy to clipboard" symbol next to the repo URL (pictured) to copy the URL.
(We'll use this in the next section.)

![github repo quick setup](https://curriculum-content.s3.amazonaws.com/web-development/enough-git-for-learn-co/github_quick_setup.png)

You can imagine that behind the scenes GitHub has `git init`'d a blank
directory.

## Demonstrate Connecting Your Local Repository of Files to Your Remote Repository

After you've created your _remote_ GitHub repository, you'll want to get your
local repository uploaded to GitHub. Follow the appropriate steps below:

#### For the In-browser Learn IDE

1. On this Learn.co lesson page, click the 'Sandbox' button to open up a blank
IDE
2. We first want to create a folder for our repository, which we'll call
`my_new_directory`, so in the terminal, type `mkdir my_new_directory`.
The folder will appear in the tree on the left of the IDE. Alternatively,
you can use the 'Create New' button at the
bottom of the IDE
4. To navigate into this new folder, type `cd my_new_directory`. Your terminal
should display `my_new_directory`, indicating that you are now inside of the
new folder
5. Next, we need to create a new file named `README.md`.  In the terminal, type
`touch README.md`.  In the file tree, if you expand the folder `my_new_directory`,
you should now see your `README.md` file. Click on it to open it in the text
editor
6. We can directly type in content here, but we can also use our terminal
skills to add content.  So, in the terminal, type
`echo "This is my readme file" > README.md`. If you've got the README file open,
the new text will appear!
7. Now that we've got some basic content, we can initialize our local
repository, so in your terminal, type `git init`.  Your terminal should show
that an 'empty Git repository' has been initialized.
8. Type `git add .` to stage the new `README.md` file so it will be tracked by `git`
9. Now, type `git commit -m 'initialize git'`.  This will create the first
commit for this local repository, which will allow us to push our work to the
remote repository we created earlier.

#### For the Standalone Learn IDE

1. Create a new directory and add a file. You can run this series of commands:
    * Change into your `code` directory: `cd ~/code`
      - If your development directory is named something other than `~/code`, that's
      fine — `cd` into whatever yours is called.
    * Create a new directory named `my_new_directory`: `mkdir my_new_directory`
    * Change into the newly-created directory: `cd my_new_directory`
    * Create a new file named `README.md`: `touch README.md`
    * Add some text to the new file: `echo "This is my readme file" > README.md`
2. Now that we've got some basic content, we can initialize our local
repository, so in your terminal, type `git init`.  Your terminal should show
that an 'empty Git repository' has been initialized.
3. Type `git add .` to stage the new `README.md` file so it will be tracked by git
4. Now, type `git commit -m 'initialize git'`.  This will create the first
commit for this local repository, which will allow us to push our work to the
remote we created earlier.

## Use `git remote` to Set the Destination of Your Repo

To connect your local repository to the newly created GitHub repository, you
must add a new remote. Adding a remote involves giving `git` a "short name" and
a "repository path." You copied the repository path from GitHub a few steps
above.

The repository path is a long bunch of technical words. The creators of `git`
thought it would be easier to type a "nickname" or a "short name" that points
to that long "repository path." It's common to have a "default" remote. The
default remote short name is called `master`. So we're going to create a new
remote with short name of `master`.

Make sure you've still got your remote git info copied from GitHub, and type
the following into the terminal:

`git remote add origin <your-copied-remote-repository-URL>`.

This sets the remote, so you can now push code.

> **ADVANCED NOTE**: It's possible to set multiple remotes. You could push to
> GitHub (short name `origin`), or a private company server (short name
> `paycheck`), or a Raspberry Pi in the living room (short name `hackMaster`).

You can use `git remote -v` to view the remote(s).

```bash
git remote -v
# View existing remotes
# origin  https://github.com/OWNER/REPOSITORY.git (fetch)
# origin  https://github.com/OWNER/REPOSITORY.git (push)
```

## Use `git push` to Send Code to the Remote Repo

Now that we have added a remote repo, we need to send our latest work the
remote.  We use this command when we want to send some code from the local
repository to the associated remote repository.  `git` will push all the local,
committed work to the remote repository.

The `git push` command takes two arguments.  The first is the name of the
remote repo. Remember, `origin` is just an alias or "short name" that refers to
the repository name. You don't actually have to enter the repository name.
Instead, you can just use `origin`. The second is the name of the remote branch
you want to send code to. In the example below, we're pushing to our remote
repository, referred to as `origin`.

```bash
git push origin master
```

> **ADVANCED NOTE**: If you have multiple remotes, you can push to multiple
> remotes.
> $ git push origin master
> $ git push paycheck master
> $ git push hackMaster master

This will push your code up to the remote repo/branch. The first time you push
code up to a newly-added remote repository, use the `-u` flag to tell Git to
"save" the remote repositiory: `git push -u origin master`.  For every
subsequent push, using `git push` will suffice.

[For more details, check out the GitHub guide on pushing.](https://help.github.com/articles/pushing-to-a-remote/)

## Conclusion

Being able to add git remotes allows you to back up your local repository to a
remote server. This will be important as you move past working on pre-existing
projects.  If you remember `git init`, `git remote add origin
your-remote-repository-URL`, add, and push your changes, you'll be able to get
your project up to GitHub in minutes!
