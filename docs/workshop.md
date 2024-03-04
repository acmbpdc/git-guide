# Git and GitHub

<center>
This is the documentation for a workshop supported by 

<a href="https://education.github.com/experts"><img src="/assets/workshop/gce_bg.jpg" style="display:block; height:30px;"></img></a>

[GCE](https://education.github.com/experts) is a global program by GitHub that looks to serve communities around the globe and support their student leaders. This session has been funded by GitHub so enjoy the pizzas, stickers and fun session!
</center>

## What is Git?

To define it technically, Git is a version control system created by Linus Torvalds in 2005 for development of the Linux kernel. Git is distributed, every directory on every computer has a working copy of the code with a complete history of changes and full version tracking capabilities.

To define it in a more fun way, Git is a multidimensional time machine! It allows you to go back in time and see what your code looked like at a certain point in time. It also allows you to collaborate with others and work on the same codebase without stepping on each other's toes.

But what is version control?

### Version Control

Let's say you are working on completing your Math-II Assignment, which requires you to write code to do some math stuff. As you keep writing your amazing code, you notice that you have to keep track of the code changes you write, so that you could come back to an old version if you mess up. As you might not be aware about VCS then, you decided to create multiple copies of your files (as shown below) to keep track of your changes.

Now you are writing the report for this project, the same situation arises, but this time you can use Google Docs' version history feature to go back in time and get your report back. This is a great example of version control.

<center>
<img src="/assets/workshop/without-vcs.png" style="width:45%"></img>
<img src="/assets/workshop/gdocs.png" style="width:45%"></img>
</center>

## So what is GitHub?

Git is to GitHub like a car is to car parking, a video is to YouTube, a photo is to Instagram. GitHub is simply a platform built to store Git repositories (folders), which allows you to store your code in the cloud, collaborate with others, and track changes to your code.

Over the years GitHub has become synonymous with developers, with so many new features added in, GitHub goes beyond simply hosting Git repositories. It has several other features such as collaboration, codespaces (Virtual Machines), web hosting, and much more.

## Getting Started

If you are using your local machine you can follow the instructions on [this page](https://git-scm.com/downloads) to install git. There are a few more steps to get your account details setup, but for today we are going to use GitHub's web interface to get started.

GitHub offers free access to a computer on the cloud, a feature known as GitHub codespaces. This is a great way to get started with coding and GitHub without having to install anything on your local machine. You can access it by clicking on the `.` key on any repository or selecting `Codespaces` on GitHub.

You will need to have or create a GitHub account to use GitHub Codespaces. If you don't have one, you can create one [here](https://github.com/signup). Please use your college email which will be useful for next steps.

Thanks to codespaces we will skip a lot of setup steps and get straight to the cool stuff. If you are referring this documentation later and need to setup git on your personal computers you can [refer this](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git).

### Creating a Repository

A repository is a place where you can store your code. It is simply the equivalent of a directory/folder. Any folder can be made into a repository. For our purposes we will be using GitHub's web interface to create a repository, this automatically makes a folder for us!

<center>
[Create a new repository](https://github.com/new)

<img src="/assets/workshop/newrepo.png" style="width:45%"></img>
</center>

Now if you return to codespaces you can [create a new codespace](https://github.com/codespaces/new).

<center>
<img src="/assets/workshop/newcodespace.png" style="width:45%"></img>
</center>

And that's it! You are ready to start experimenting. This interface is a web version of the popular IDE (Integrated Development Environment) Visual Studio Code. You can write code, run it, and do everything you would do on your local machine. And since it is integrated by GitHub, there is no need for extra logins or authentication.

<br>
<center>
**YOU DO NOT NEED A GITHUB ACCOUNT TO USE GIT!**
</center>

This is a common misconception. You can use git on your local machine without ever needing to create a GitHub account. However, if you want to collaborate with others, or store your code on GitHub, you will need a GitHub account. In our case, we are using GitHub's virtual machines (borrowing their laptop on your browser) so we want to use GitHub. 

You can now make use of the terminal on the bottom of the screen to work with git. You can navigate, create and edit files, folder by clicking on the directory on the left.

## The Basics

### `init`

To make any directory into a git repository, use the `init` command.

```sh
git init
```

You might see the `Reinitialized existing Git repository` message, this simply means that this folder is already a git repository. When we create a repository on GitHub it is already git *init-ed*.

If you view hidden files, you can see a new folder called `.git` created. This is where git stores all the information that git needs to track your project (*you really don't have to know what any of the things inside this directory does, to use git*). 

### `add`

Once you are done writing code, let's start the next step of tracking our repository. 

Git has this special place allocated to review the changes you have in the files you have added, changed or deleted, called as the **Staging Area**. 

To add files into the staging area, use the `add` command.

```sh
git add file1
```

To add all the files in your repository (*recursively*), use `.` to indicate all files. Be careful while using this, as you might not always want to add all the files to your staging area.

```sh
git add .
```

#### Staging Area

The staging area contains all of the information about what files and changes are going into the next snapshot of the repository.

Files inside a `git` repository are of two types:

- **Untracked**: These files are the new files that you add into your repository, that git still haven't started tracking. 
- **Tracked**: These files are the ones' that git is already keeping track of. These files could either be:

    - **modified**: This means that we have made changes into the tracked file, but it has not yet been staged or committed. Git won't notice these files until we *stage* these files. Note that even if you had used `git add` on this file earlier, it will return to the modified state if you make changes to it.
    - **staged/tracked**: These are *modified* files which are ready to be committed (*added into the next snapshot of the repository*). 
    - **committed**: The changes of these files are stored into the `git` repository, after the snapshot is taken.

To understand the current file tracking statuses use

```sh
git status
```

Git status is a very useful command to understand what is happening in your repository. It will tell you what files are untracked, modified, staged, and committed. As well as give you suggestions on commands that you can use.

### `restore`

To remove files or directories from the staging area, use the `restore` command. This will bring it back to the untracked state.

```sh
git restore --staged file1
```

You can also `restore` command to discard all the **unstaged** local changes made to your files in your repository. This will bring the file back to the last committed state.

```sh
git restore .
```

`restore` command is also used to restore a file to how it was in a previous commit.

```sh
git restore --source=HEAD file1
```

### `commit`

Once you are done reviewing the changes you want in the next snapshot of your repository, you are now ready to click that snapshot. 

To click save this state, use the `commit` command.

```sh
git commit -m "My first commit!"
```

You can also type a short commit message directly from this command, by using the `-m` flag. Or to write a more detailed message, just use `git commit`. This will open up a text editor where you can write a detailed message. It is recommended to write a detailed message, as it will help you understand what you did in the future.

### `diff`

Sometimes, before you stage your code, you would want to inspect the changed code. To see the *difference* between the old and new versions of your file, use the *diff* command.

```sh
git diff
```

This command will only show you the changes made to unstaged files.

To see the changes made in staged files, use `--staged` flag.

```sh
git diff --staged
```

### `log`

To inspect the history of the commits made in a `git` repository, use the `log` command.

```sh
git log
```

You would be seeing an output as shown below

```sh
commit 227fbdb4ef3a05b2df0dfdc4fbea61e2d13af044 (HEAD -> main)
Author: The Real Thanos <thanos.cool@email.com>
Date:   Thu Nov 25 00:11:14 2021 +0400

    Collect Power Stone
```

The huge string that you see along with `commit` is a commit's number. It is a 40-character hexadecimal string, which uniquely identifies a commit.

**main**: This refers to the final *branch* in your git repository (*More about branches discussed later in this documentation*). 

**HEAD**: This refers to the current branch pointed by git.

**origin**: This refers to the remote repository that you have set. (*More about remotes discussed later in this documentation*). 

To see the `log` in a concise manner, use the `--oneline` flag.

```sh
git log --oneline
```

### Branches

What if you are working as a Software Development Engineer at Google, on their Maps Application, and you had to develop a feature to find the time taken by a kite to follow the directions to a location? Would you directly make changes to the deployed application, to implement your feature? Or would you try to play it safe and make sure your feature is all good, before you add it to the deployed application?

You might probably choose the second option. That is where *branches* come in!

**Branching** allows you to create a copy (*branch*) of your current working directory, and make changes (*commits*) to this copy, without disturbing anything else.

<div align="center">
    <img src="/assets/workshop/git-branch.png">
</div>
</br>

The *default* branch that git creates for you, when a new repository is created (`init`) is called **main**.

To **see all the branches** in your repository, use the `branch` command

```sh
git branch
```

To **create a new branch**, add the new branch name along with `branch` command.

```sh
git branch kite-feature
```

To **switch to different branch**, use the `checkout` command.

```sh
git checkout kite-feature
```

To **create a branch and switch the branch at the same time**, use the `-b` flag along with `checkout` command.

```sh
git checkout -b kite-feature
```

To **delete a branch**, use the `-d` flag along with `branch` command.

```sh
git branch -d kite-feature
```

#### Merge 

To **merge** the changes between branches, use the `merge` command.

```sh
git merge from_which_branch_to_merge_from
```

<div align="center">
    <img src="/assets/workshop/git-merge.png">
</div>
</br>

#### Merge Conflicts

Merge Conflict is the problem that occur when Git is unable to automatically merge branches (*or commits*).

When merging a branch, where all changes occur on different lines or in different files, Git will automatically be able to merge them.

A conflict occurs when the changes made occur on the same line, as Git won't be able to figure out which change to keep, and which change to discard.

You can make use of GUI features inbuilt to VSCode and other editors to help resolve these.

There are a lot more awesome commands and features in Git, you can refer the basics on your cheatsheet. Find great [resources attached](#resources).

### Remotes

A remote repository in Git, also called a remote, is a Git repository that’s hosted on the Internet or another network. (*It's basically like how you could host your pictures or folders on Google Drive*)

This is where **GitHub** really comes into picture! Few other popular examples of remotes are **BitBucket** and **GitLab**.

<details><summary>For Local Machines</summary><pre>
To set up your GitHub user with your `git`, add your GitHub username to `config`.

```sh
git config --global user.name "HalfTheWorldSlayer"
```

To save your password for later, enter the following command

```sh
git config --global credential.helper store
```
</pre></details>

#### Adding Remotes to Git Repo

<details><summary>For Local Machines</summary><pre>
To add a remote to a repository that you have in your local system, use the `remote` command. 
You can get the remote url from GitHub itself by clicking on the `Code` button and copying the url.
When you create a blank repository on GitHub you will get a list of initiation commands, you can use those to get started locally.

```sh
git remote add origin {remote_url}
```
</pre></details>

In our case we have the remote already set up for us, so we don't have to worry about this. You can check this with

```sh
git remote -v
git remote get-url origin
```

`origin` as mentioned in the command, is the name we are calling for the remote we just added. We can set the name to be anything as we please. Origin is merely the convention used by most developers.

#### `push`

To update the commits you made on your local system or even GitHub's VM codespaces, to your remote (*GitHub*), use the `push` command.

```sh
git push origin main
```

While pushing a new `feature` branch onto remote, `-u` should be used. This will set the upstream branch for the feature branch. (create the branch on the central remote repository)

```sh
git push -u origin kite-feature
```

To delete a branch from the remote, use the `--delete` flag.

```sh
git push --delete origin kite-feature
```

Until you use `git push` no changes will be synced with your repository on GitHub. Till then everything remains local. Ensure you have completed your work before you push so any other viewers can make sense of your code.

#### `clone`

To *clone* a repository which is hosted on a remote, use the `clone` command.

```sh
git clone {repo_url}
```

We cannot use it now because we are already in a repository. But if you want to try it out, you can do it on your own machines. This command is commonly used to access code on the internet or even to access your own repository that you might have created on GitHub first.

#### `pull`

To retrieve the changes made in the remote, but not in the local, use the `pull` command. We would use this command when we are working on a project with multiple people, and we want to get the latest changes made by others that they have pushed to the remote.

```sh
git pull origin main
```

(*This command is used instead of using `fetch` and `merge`, as it fetches the changes and updates the local as well.*)

## Open Source

Imagine you're baking a cake with your friends. Open source is like sharing your cake recipe with everyone and inviting them to help bake it together. 🎂

GitHub is where you share your recipe (code) with others. People can see your recipe, suggest improvements, or even bake their own version of the cake! 🍰

So, in simple terms, open source on GitHub means sharing your code with others, collaborating together, and making cool stuff for everyone to enjoy! 🚀

### Forks

A way of creating a copy of a given repository, so that it belongs to our user. This let's you work on a copy of any code that you see on *GitHub*. 

<div align="center">
    <img src="/assets/workshop/fork.png">
</div>
</br>

### Pull Requests

A commit or series of commits that you send to the owner of a repository, so that they incorporate your code commits into their actual tree.

### Do It Yourself - Contribution Workflow

*Win a sticker for your first contribution! IRL and on your profile!*

- **Step 1**
<br>Create a fork of the [repository we setup for you to learn](https://github.com/acmbpdc/learning-open-source).

- **Step 2**
<br>Open the forked repository in GitHub codespaces. You can find your fork on your GitHub profile, repositories tab: https://github.com/{YOUR USERNAME HERE}?tab=repositories. Open the forked repository and press the `.` button to open in codespaces. Alternatively you can open a [new codespaces instance](https://github.com/codespaces/new) and select the forked repository.
<details><summary>For local machines</summary><pre>If you have your own laptops you should `git clone` and work on the repository locally.</pre></details>

- **Step 3**
<br>Follow the steps given in the README, create and checkout a new branch in your clone to start working on the code you want to add.

- **Step 4** 
<br>Add the file into that branch naming it with the format provided.

- **Step 5** 
<br>Once done making changes, add and commit the changes.

- **Step 6** 
<br>Once all the commits are made, you can now `push` the changes to your fork, in the remote.

- **Step 7** 
<br>You can now create a pull request from your fork, on your remote (*GitHub*), onto the actual repository. Open the fork url on GitHub and click on the `Pull Requests` tab and then `New Pull Request`. You may also use the prompt on screen:

    - Click on `Compare & pull request`.
    - Create a pull request.
    - Once the maintainer of the repository reviews your code, they'll merge your code into their repository.

---

**YAY!** *You just made your first contribution!* 🎉

This was a simple example. But doing it yourself prepares you to contribute to any open source project on GitHub. You can [explore repositories on GitHub](https://github.com/trending) and contribute to any that interest you. We welcome contributions to any of ACM's open source documentation projects: [Openlib.cs](https://github.com/acmbpdc/openlib.cs), [Truffle](https://github.com/acmbpdc/Truffle).

We have some helpful tips and workflows below for your reference.

## Git Workflow

A quick way to get started with basic git.

**Step 1**: You start off by creating a git repository (`init`).

**Step 2**: Write all the code you need into this repository (`code`).

**Step 3**: Once you are done writing/editing code, we add the new/changed files into a special place called as the *staging area* (`add`).

**Step 4**: Once you review your changes, you will now take a snapshot of the repository (`commit`).

**Step 5**: If you have new changes to make into your repository, continue the workflow from *step 2*.

### Best Practices for Git

- **Don't make small commits**: You really don't have to make a commit every time you make a change in a file. 
- **Don't make huge commits**: Rather than committing the entire project at once, it's the best to commit every time you hit a checkpoint (**eg:** *Implements a function for your OOPs Project*)
- **Write Proper Commit Messages**: When writing a commit message, make sure to write meaningful commit messages (*rather than just* "Update file1")

## Contribution Workflow

A quick reference for working with distributed repositories.

**Step 1**: Create a fork of the repository that you want to work on.

**Step 2**: Clone the fork into your local system.

**Step 3:** You could create a new branch in your clone to start working on the code you want to add.

**Step 4:** Make all the changes you want into that branch.

**Step 5:** Once done making changes, commit the changes.

**Step 6:** Once all the commits are made, you can now `push` the changes into your fork, in the remote.

**Step 7:** You can now create a pull request from your fork, on your remote (*GitHub*), onto the actual repository.

### Best Practices for Contribution/Collaboration

- Always synchronize your branches before starting any work on your own.
- Avoid having very large changes that modify a lot of different things.
- When working on a big change, it makes sense to have a separate feature branch.
- Regularly merge changes made on the main branch back onto the feature branch.
- Have the latest version of the project in the main branch, and the stable version of the project on a separate branch.
- Having good commit message is important.

## GitHub Student Developer Pack

<center>
<img src="/assets/workshop/backpack.png" style="width:45%">
</center>

There's no substitute for hands-on experience. But for most students, real world tools can be cost-prohibitive. That's why GitHub created the [GitHub Student Developer Pack.](https://gh.io/acm-pilani)

There are a few steps we need to complete before we can apply for the pack. Follow the links below and complete the steps to access 100's of amazing resources and tools for free including GitHub Pro, GitHub CoPilot AI, AWS, Azure credits, free domains, several free trials and so much more! As an added benefit grab an extra sticker for applying for the pack!

- [Update your location information, ensure you press save](https://github.com/settings/billing/payment_information)
- [Ensure your college mail has been verified](https://github.com/settings/emails)
- [Enable 2FA and activate it](https://github.com/settings/security)
- [Customise your GitHub profile](https://github.com/settings/profile)
- [Add a profile README, you should see a prompt for the same](https://github.com)

<img src="/assets/workshop/rme.png"></img>

<details><summary>If you don't see the highlighted prompt</summary>
<pre>
- Go to [New Repository](https://github.com/new)
- Set the repository name same as your username (you will see a message telling you this is a special repository)
- Add a README file
Enter the following in the file:
```md
- 👋 Hi, I’m @USERNAME
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
```
</pre>
</details>

Use this referral link to get access quickly! [https://gh.io/acm-pilani](https://gh.io/acm-pilani). And start enjoying the benefits!

## Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Learn Git Branching](https://learngitbranching.js.org/) - Interactive lesson which visualises branches and commits
- [Understanding Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) - An intuitive markup language used to format text
- [Need help - Fast!](https://ohshitgit.com/)
- [Git for Beginners (recommended)](https://www.youtube.com/watch?v=apGV9Kg7ics)
- [Git for Beginners](https://www.youtube.com/watch?v=8JJ101D3knE)

And stay tuned for Git Guide's launch - a comprehensive guide to Git and GitHub!