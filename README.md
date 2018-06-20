# Git Remotes + GitHub

## Problem Statement

GitHub does nothing special in the git universe. It's just another git
repository in the cloud. Creating remote repositories on GitHub is very handy
if you're ever working on a project while using multiple computers, and is
especially helpful if you're working on a project with others. If you don't
want to work with anyone else, you may not need remotes, but, in our case, we
want to work with others! So, we have to talk about remotes.

## Objectives

1. Explain creating a remote repository on GitHub
2. Demonstrate connecting your local repository of files to your remote repository
3. Use `git remote` to set the destination of your repo
4. Use `git push` to send code to the remote repo
5. Use `git pull` to retrieve code from the remote repo
6. Use Github to make direct edits


## Explain Creating a Remote Repository on GitHub

1. While logged into GitHub, in the upper right corner, click the **+** in the
menubar and select `New repository`. Alternatively, you can navigate to [github.com/new](https://github.com/new).
2. Enter a name for your repository in the `Repository name` field. You can
name it whatever you'd like; be creative! The default options are fine as-is —
don't initialize the new repository with a README or add a `.gitignore` or
license. Click the green `Create repository` button.
3. After you create the repo, you should see a "Quick setup" page. Click the
"Copy to clipboard" symbol next to the repo URL (pictured) to copy the URL.
(We'll use this in the next section.)

![github repo quick setup](https://curriculum-content.s3.amazonaws.com/web-development/enough-git-for-learn-co/github_quick_setup.png)

## Demonstrate Connecting Your Local Repository of Files to Your Remote Repository

What is `origin`? "Origin" is simply the default alias assigned to your new
remote repo, but we could rename it to anything. Let's try changing the name of
the repo to `destination`:

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
remote, so you can push and pull code.

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
remote, so you can push and pull code.


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

For consistency's sake, let's go ahead and rename `destination` back to `origin`:

```bash
git remote rename destination origin
```

## Use `git push` to Send Code to the Remote Repo

Now that we added a remote repo, we need to send our latest work the remote.

We use this command when we want to send some code from the local repository to
the associated remote repository.

The `git push` command takes two arguments. The first is the name of the remote
repo. Remember, `origin` is just an alias that refers to the repository name.
You don't actually have to enter the repository name. Instead, you can just use
`origin`. The second is the name of the remote branch you want to send code to.
In the example below, we're pushing to the master branch of our remote
repository, referred to as `origin`. To find all the remote branch names, run
`git branch -r`.

```bash
git push origin master
```

That is the explicit way to push. You can also implicitly push your code by running:

```bash
git push
```
This will push your code up to the remote repo/branch you're tracking. The
first time you push code up to a newly-added remote repository, use the `-u`
flag to tell Git to track the remote repository: `git push -u origin master`.
For every subsequent push, plain old `git push` will suffice.

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

## Use Github to Make Direct Edits

Say you liked your README, but you noticed a minor typo. Let's fix it directly on GitHub.

1. Navigate to your remote repository on [GitHub.com](https://github.com/), e.g., https://github.com/username-here/repository-name-here.
2. Click on your README file.
3. At the top of the file, you'll notice a pencil icon (![GitHub pencil](http://i.imgur.com/J3HiLhO.png)). Clicking this will allow us to edit the file.
4. Make some changes to your README.
5. Commit them by clicking the "Commit changes" button at the bottom of the page.

Perfect! But now the code on our machine (in our local repo) is out of sync with the remote repo. To remedy this, we must `pull` down the code to our local repo. To do so, run:

```bash
git pull
``` 

## Conclusion

Being able to add and update git remotes allows you to be able to get repos started up
from scratch. This will be important as you move past working on pre-existing projects.
If you remember `git init`, `git remote add origin your-remote-repository-URL`, add, and
push your changes, you'll be able to get your project up to github in minutes!

[For more details, check out the GitHub guide on pulling.](https://help.github.com/articles/fetching-a-remote/)

<p data-visibility="hidden">View <a href="https://learn.co/lessons/git-remotes-with-github-readme" title="Git Remotes + GitHub">Git Remotes + GitHub</a> on Learn.co and start learning to code for free.</p>
