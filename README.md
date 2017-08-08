# Git Remotes + Github

## Objectives
1. Describe Github and its relationship with Git
2. Create a remote repository on GitHub
3. Use `git push` to connect your local repository of files to your remote repository
4. Use `git remote`
5. Use `git push`
6. Use `git pull`

## Why this is useful
GitHub does nothing special in the git universe. It's just another git repository in the cloud. If you don't want to work with anyone else, you don't need remotes. However, this is rarely the case, and we want to work with others! So, we have to talk about remotes.

## Creating a remote repository on GitHub
1. From your GitHub profile, click the "Create New Repository" button.
2. After you create the repo, you should see a "Quick setup" page. Click the "Copy to clipboard" symbol next to the repo URL (pictured) to copy the URL. (We'll use this in the next section.)

![github repo quick setup](https://curriculum-content.s3.amazonaws.com/web-development/enough-git-for-learn-co/github_quick_setup.png)

## Connecting your remote repo to a local repo
1. Create a new directory and add a file if you haven't already. You can run this series of commands:
    * Change into your `code` directory: `cd ~/code`
      - If your development directory is named something other than `~/code`, that's fine — `cd` into whatever yours is called.
    * Create a new directory named `my_new_directory`: `mkdir my_new_directory`
    * Change into the newly-created directory: `cd my_new_directory`
    * Create a new file named `README.md`: `touch README.md`
    * Add some text to the new file: `echo "This is my readme file" > README.md`
2. `git init`
3. `git add .` + `git commit -m "initialize git"`. Add and commit the new file created by the `git init` command in step 1.
4. `git remote add origin your-remote-repository-URL`. This sets the remote, so you can push and pull code.

### Note on Origin
What is `origin`? "Origin" is simply the default alias assigned to your new remote repo, but we could rename it to anything. Let's try changing the name of the repo to `destination`:

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

## `git push` + `git pull`

Now that we added a remote repo, there are two actions. We can send our latest work to and retrieve the latest work from the remote.

### `git push`

We use this command when we want to send some code from the local repository to the associated remote repository.

`git push` takes two arguments. The first is the name of the remote repo. Remember, `origin` is just an alias that refers to the repository name. You don't actually have to enter the repository name. Instead, you can just use `origin`. The second is the name of the remote branch you want to send code to. In the example below, we're pushing to the master branch of our remote repository, referred to as `origin`. To find all the branch names, run `git branch -r`.

```bash
git push origin master
```

That is the explicit way to push. You can also implicitly push your code by running:

```bash
git push
```
This will push your code up to the remote repo/branch you're tracking.

[For more details, check out the GitHub guide on pushing.](https://help.github.com/articles/pushing-to-a-remote/)

### `git pull`

As we collaborate with other people, inevitably they will push some code. The only problem is that now the code on our machine (our local repo) is out of sync with the remote repo. To remedy this, we must pull down the new code from the remote repo to our local. No surprise here. To do this, run:

```bash
git pull
```

Again, we can also do this explicitly if need be by adding the remote name and branch as arguments: `git pull origin master`.

[For more details, check out the GitHub guide on pulling.](https://help.github.com/articles/fetching-a-remote/)

<p data-visibility="hidden">View <a href="https://learn.co/lessons/git-remotes-with-github-readme" title="Git Remotes + GitHub">Git Remotes + GitHub</a> on Learn.co and start learning to code for free.</p>
