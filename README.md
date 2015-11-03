#Git Remotes + Github

##Objectives
1. Describe Github and its relationship with git
2. Create a remote repository on Github
3. Use git push to connect your local repository of files to your remote repository 
4. Use git remote
5. Use git push
6. Use git pull


##Why this is useful
Github does nothing special in the git universe. It's just another git repository in the cloud. If you don't want to work with anyone else, you don't need remotes. However, this is rarely the case, and we want to work with others! So, we have to talk about remotes. 

##Creating a remote repository on Github

1. From your Github profile, click the "Create New Repository" button.
2. After you create the repo, click the "Copy to clipboard" symbol on the right-hand side of the screen to copy the url (we'll use this in the next section)


##Connecting your remote repo to a local repo
1. `git init`
2. `git add .` + `git commit -m "initialize git"`. Add and commit the new file created by the init command in the step 1.
3. `git remote add origin your-remote-repository-URL`. This sets the remote, so you can push and pull code.

###Note on Origin
What is `origin`? Origin is just the name of the repo, but it could be anything. Origin is simply a convention for the default repo name. Let's take a closer look by changing the name of the repo:

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

##git push + git pull
Now that we added a remote repo, there are two actions. Send our latest work up and retrieve the latest work from the remote. 

###git push
We use this command when we want to send some code from the local repository to the associated remote repository.

`git push` takes two arguments. The first is the name of the remote repo. The second is the name of the remote branch you want to send code to. To find the names, run `git branch -r`. 

```bash
git push origin master
``` 

That is the explicit way to push. You can also implicitly push your code by running:

```bash
git push
``` 
This will push your code up the remote repo/branch you're tracking.

[For more details, check out the Github guides on pushing](https://help.github.com/articles/pushing-to-a-remote/)
Then explain push and pull (show explicit, then show that by default it's called origin/master).

###git pull
As we collaborate with other people, inevitably they will push some code. The only problem is that now our code on our machine (our local repo) is out of sync with the remote repo. To remedy this, we must pull down the code to our local repo. No surprises here. To do this we run:

```bash
git pull
``` 

Again, we can also do this explicitly if need be by adding the remote name and branch as arguments: `git pull origin master`.

[For more details, check out the Github guides on pulling](https://help.github.com/articles/fetching-a-remote/)
