# bye_master
While GitHub is [working on changing the default conventions it
uses](https://www.cnet.com/news/microsofts-github-is-removing-coding-terms-like-master-and-slave/),
notably the use of a default `master` branch, I wanted to create this simple
repository to demonstrate how you can change your default GitHub branch already.

## Creating a new default branch to replace auto-generated default `master` 

When I created this repository through the GitHub interface, it generates
various defaults and basic `git` infrastructure/initialization.  GitHub uses the
very common (to date) convention of a default `master` branch.

To change the default branch, I first clone to my local machine
```
$ git clone git@github.com:adam-m-jcbs/bye_master.git
```

Now I rename the local version of the branch (this command applies to the
current branch you are on, in this case `master`)
```
git branch -m main
```

I now push this renamed branch to GitHub and tell `git` that our now upstream
branch is now `main`.  You will get an error, but that's OK
```
git push origin :master main
git push origin -u main
```

`git` will tell you that GitHub refused to delete the `master` branch.  That's
because it's still configured as the default branch.

So, we got the the repo's Settings --> Branches in order to set the default
branch as our new `main` branch.

![GitHub Branch Settings](/images/Screenshot_GitHubDefaultBranchSetting.png)

Finally, delete the now-irrelevant `master` branch
```
git push origin --delete master
```

This guide made use of [this helpful
tutorial](https://www.hostinger.com/tutorials/how-to-rename-a-git-branch/).
