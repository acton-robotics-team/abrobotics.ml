# The Basics of Git

## Getting Set-Up

Go to this [link](https://git-scm.com/downloads) and download the latest version of git for your OS. Click the file you download and follow the prompt. Do not alter the setting.

## Downloading the Repository

To navigate the repository on your own computer, you need to know a few basic functions of git. To start of, if you want to download the repository, or in git terms: "clone" the repository, use the following command

`$ git clone /path/to/repository`

If you're using github, it's really easy to find the link. Go to the repository page, and click the green clone "Clone or download" button. A window will pop up, then click the copy button:

![Directory](https://i.imgur.com/5V8oLro.png)

Run the `git clone` command with the link you copy, and it will begin to download the repository. Once downloaded, you can start making changes.

## Proposing changes

### Staging Changes

Well now you've made your changes, how do you push your changes to the repository? Go to your terminal or go to the git bash and navigate to the directory where you cloned the repository (us the `ls`, `cd` and `pwd` commands if you don't know already). Once you're there, use the following command:

`$ git status`

You will see a list of all your changes, which will look like this:
![Git Status](https://i.imgur.com/YRPcFeW.png)

If you are happy with the changes, run the following commands.

`$ git add *`

or

`$ git add .`

The only difference between the two is that the `.` includes files that start with a `.`. For the most part use the first one. If there is a specific file you want to push, use the following command

`$ git add filename`

Now your changes are staged, run git status again to see your changes.

![Git Status Staged](https://i.imgur.com/H8rLGJk.png)

### Commiting

Time to commit. There are two ways to commit a file, one is easier while the other gives you more info and lets you add more details. Make sure your message is descriptive enough so anyone who reads it can understand it.

Option 1:
`$ git commit -m "enter your commit message here"`

Option 2:
`$ git commit -a`

If you use option 1, then you're all set. If you used option 2, you'll have to use vim. Don't worry, it's not scary. Your screen should look like this:

![VIM](https://i.imgur.com/fFGffBk.png)

On your keyboard, type `Esc + i` to go into insert mode. Type in your commit message. Once you are done, type the following: `Esc + :wq` and then enter. Now you're all set too!

### Push Your Changes

Now for the final step, pushing your changes. Run the following command:

`$ git push origin master`

You might run into something called a "merge error" which sometimes are a huge headaches, and otherwise they are simple edits. If you get one of these errors, look at it's section under the Advanced Topics Section.

### Pulling Changes

If someone makes changes and pushes, then you want to pull their changes. This is very simple. Make sure you are on the same branch as them, and then use the following command:

`$ git pull`

If you want to pull, you will need to commit your changes (not push). If you see merge conflicts, check the merge conflict sections in the Advance Topics section.

## Advanced Topics

### Branches

Git repositories can have multiple "branches". These branches can be developed independently with each other. Here we use them to separate our software between competition years. If you want more info on branches, click [here](https://git-scm.com/book/en/v1/Git-Branching-What-a-Branch-Is). All you need to know is how to switch between branches. If you want to see the list of branches and what branch you are currently on, use the following command:

`$ git branch -a`

Your command-line should like this:

![git branch -a](https://i.imgur.com/yLOfRn6.png)

If you want to switch git branches, use the following command:

`$ git checkout <branch_name>`

That's it!

### Merge Conflicts

Sometimes you might have made changes in the same file as someone else. Git won't know which one to keep, so it will throw a merge error. If you do, go to the file(s) where the merge conflicts occured, and you will see edits made to the file by git. The start of the merge error will begin with a large number of `<` characters followed by `HEAD`. There will be a set of `=` between the two different versions, and it will end in a load of `>` characters and a strong of letters and numbers. Delete the version that you don't want, and then delete all of the lines inserted by git. That's it! Now push.

If you are still confused, click [here](http://genomewiki.ucsc.edu/index.php/Resolving_merge_conflicts_in_Git).

### Fetching

Say you messed up, and you want to reset a file. This is where you can use fetching. If you want to replace your changes for a single file, use the following command:

`$ git checkout -- <filename>`

If you want to discard _all_ of your changes, including non pushed commits, use the following commands:

`$ git fetch origin`

and then,

`$ git reset --hard origin/master`

### Log

The log function is useful if you want to see the commit history of a repository. To see the history, use the following command

`$ git log`

That will look like this:

![git log](https://i.imgur.com/XVcmafH.png)

To exit, type `q`. Sure that's cool, but that looks terrible. Luckily we have a solution. Run the following

`$ git config --global -e`

It should look like this:

![config](https://i.imgur.com/3yNcarE.png)

Now copy the following line:

```(bash)
[alias]
    logg = log --graph --pretty=tformat:'%Cred%h %Cgreen%cd %C(bold blue)%an%Creset%C(yellow)%d%Creset %s' --date=short --all
```

Go back to your bash, and type `Esc + i` to start editing. Create a new line, and delete the extra tab. Paste the lines above using `shift-insert` on windows. Your editor should look like this:

![config edited](https://i.imgur.com/ySn5ATe.png)

Now to save and exit, type `Esc + :wq`. From now on, do **not** use `git log` or else it will still look the same. Use the following.

`$ git logg`

It will now look like this:

![git logg](https://i.imgur.com/6i0UWSw.png)

To exit, type `q`. That's it!

## Miscellaneous

### Git GUI

Github comes with a GUI. It can be used to easily view differences between commits. Use the following command:

`$ gitk`

It should look like this:

![gitk](https://i.imgur.com/gQvQY8d.png)
