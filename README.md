# Git Remotes + GitHub

## Problem Statement

As strange as it may seem, GitHub does nothing special in the git universe. 
It's just another git repository in the cloud. A repository that's non-local
is called a _remote_. You've seen how valuable _remotes_ are for _getting_
software. Let's learn about the other side of the equation: let's learn to
mirror our _local_ repository to a _remote_ using `git push` and `git remote`.
Once your code is on a _remote_, it's backed up &mdash; which is always a good
thing &mdash; and it's available for _someone else_ to `fork` or `clone` and
benefit from. You might see the hint of a collaboration model there. We'll
talk about collaboration soon, but first, let's learn how to `push` our code!

## Objectives

1. Explain creating a remote repository on GitHub
2. Demonstrate connecting your local repository of files to your remote repository
3. Use `git remote` to set the destination of your repo
4. Use `git push` to send code to the remote repo
5. Use `git pull` to retrieve code from the remote repo


## Explain Creating a Remote Repository on GitHub

1. To create a new repository, go to: [github.com/new](https://github.com/new),
while logged into GitHub.
2. Enter a name for your repository in the `Repository name` field. You can
name it whatever you'd like; be creative! The default options are fine as-is —
don't initialize the new repository with a README or add a `.gitignore` or
license. Click the green `Create repository` button.
3. After you create the repo, you should see a "Quick setup" page. Click the
"Copy to clipboard" symbol next to the repo URL (pictured) to copy the URL.
(We'll use this in the next section.)

![github repo quick setup](https://curriculum-content.s3.amazonaws.com/web-development/enough-git-for-learn-co/github_quick_setup.png)

## Demonstrate Connecting Your Local Repository of Files to Your Remote Repository

After you've created your GitHub repository, you'll want to get your local repository
uploaded to GitHub. Follow the appropriate steps below":

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
8. Type `git add .` to stage the new `README.md` file so it will be tracked by git
9. Now, type `git commit -m 'initialize git'`.  This will create the first
commit for this local repository, which will allow us to push our work to the
remote we created earlier.
10. Now, make sure you've still got your remote git info copied from GitHub,
and type the following into the terminal:
`git remote add origin <your-copied-remote-repository-URL>`. This sets the
remote, so you can push code. The `git remote add` command consists of a 
remote name, by default, origin and a remote URL such as https://github.com/user/repository-name.git. The remote name _origin_ is
the default alias assigned to your new remote repo. It can be renamed
to anything. 

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
5. Now, make sure you've still got your remote git info copied from GitHub,
and type the following into the terminal:
`git remote add origin <your-copied-remote-repository-URL>`. This sets the
remote, so you can push code. The `git remote add` command consists of a
remote name, by default, origin and a remote URL such as https://github.com/user/repository-name.git. The remote name _origin_ is
the default alias assigned to your new remote repo. It can be renamed
to anything.

## Use `git remote` to Set the Destination of Your Repo

```bash
git remote -v
# View existing remotes
# origin  https://github.com/OWNER/REPOSITORY.git (fetch)
# origin  https://github.com/OWNER/REPOSITORY.git (push)

git remote rename origin destination
# Change remote name from 'origin' to 'destination'

git remote -v
# Verify remote's new name
# destination  https://github.com/OWNER/REPOSITORY.git (fetch)
# destination  https://github.com/OWNER/REPOSITORY.git (push)
```

Let's rename `destination` back to `origin`:

```bash
git remote rename destination origin
```

## Use `git push` to Send Code to the Remote Repo

Now that we added a remote repo, we need to send our latest work the remote.
We use this command when we want to send some code from the local repository to
the associated remote repository. The `git push` command takes two arguments.
The first is the name of the remote repo. Remember, `origin` is just an alias
that refers to the repository name.You don't actually have to enter the
repository name. Instead, you can just use `origin`. The second is the name
of the remote branch you want to send code to. In the example below, we're
pushing to our remote repository, referred to as
`origin`.

TO implicitly push your code, you can run:

```bash
git push
```
To `explicitly` push your changes, you can use:

```bash
git push origin master
```

This will push your code up to the remote repo/branch. The
first time you push code up to a newly-added remote repository, use the `-u`
flag to tell Git to "save" the remote repositiory: `git push -u origin master`.
For every subsequent push, using `git push` will suffice.

[For more details, check out the GitHub guide on pushing.](https://help.github.com/articles/pushing-to-a-remote/)


##  Use `git pull` to Retrieve Code from the Remote Repo

As we collaborate with other people, inevitably, they will push some code. The
only problem is that once this happens, the code on our machine (our local
repo) will be out of sync with the remote repo. To remedy this, we must pull
down the new code from the remote repo to our local. No surprise here. To do
this, run:

```bash
git pull
```

In our case, running `git pull` should return the message `Already up-to-date.`,
since our remote hasn't been modified.  If there was new content, the terminal
will show that it is unpacking and updating, then list out any files that have
been updated.

Again, we can also do this explicitly if need be by adding the remote name and
branch as arguments: `git pull origin master`.

[For more details, check out the GitHub guide on pulling.](https://help.github.com/articles/fetching-a-remote/)

## Conclusion

Being able to add and update git remotes allows you to back up your local repository to a remote server. This will be important as you move past working on pre-existing projects.
If you remember `git init`, `git remote add origin your-remote-repository-URL`, add, and
push your changes, you'll be able to get your project up to GitHub in minutes!

[For more details, check out the GitHub guide on pulling.](https://help.github.com/articles/fetching-a-remote/)

<p data-visibility="hidden">View <a href="https://learn.co/lessons/git-remotes-with-github-readme" title="Git Remotes + GitHub">Git Remotes + GitHub</a> on Learn.co and start learning to code for free.</p>
