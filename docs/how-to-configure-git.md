# How to configure Git

## What is Git

Git is a open source version control. It works by keeping track of changes of the changes in a file.  
You may be asking yourself which files are under the control of git and if it may accidentally start tracking unwanted files. The short answer is `NO`. This is because Git only keeps track of all the file in the folder it was initialized in and it's children. The only exception is the files that are in a special folder named `.gitignore`.

There are a couple of methods to configure Git in your sandbox or *nix environment. One of the methods is to use the CLI (Command Line Interface) and the other one is to edit the `.gitconfig` file directly. We will go over both of this methods.

## Configure Git using the CLI

This is by far the most used method in configuring git. It is easier and less error prone.

The `--global` flag that we'll be using tells git that we want the setting to be applied system wide not just in the current folder/repository/directory.

Now let's configure the most common settings that we will be using most of the time.

### Configure your Name

```bash
git config --global user.name "Your name"
```

>> We first start configure the name that will be used in our git operations. The name can be anything. But the you should choose either your name or a name that most people know. This can help your team know who performed an operation. You don't have to use the quotes if you are using one name, but if it is more than one then you have to use them. If my username is `Gekko Wrld` then I can do it like this.

```bash
git config user.name "Gekko Wrld" # For more than one name
git config user.name GekkoWrld # For one name/word
```

### Configure your Email

```bash
git config user.email "your@email.com"
```

>> Here their are some options to choose from. Since we will be working with `Github` we have two options. You can choose to enter your real email e.g if my email is `gekko_wrld123@email.com` then I can use the following command.

```bash
git config --global user.email gekko_wrld123@email.com
```

>> But if you want you can use your private email. This is an email that Github gives you if you opt to make your email private. It usually has some digits and github as the host name. If I opted to a personal email, then the steps are the same, only the email will change. You can find the email under `settings` then navigate to `Emails` and look for the email that is provided by Github.

```bash
git config --global user.email 123456376+gekkowrld@users.noreply.github.com
```

### Configure other settings

Now we will go over some settings that are not mandatory and can be skipped altogether during git configuration.

#### Color

Let's begin with color, this will be the color in which git will display it's output in.

Git supports several color options that you can use to customize the output in your terminal. Here are some examples:

- "normal": This is the default color for text output in Git. It is typically the same color as the terminal's default text color.

- "black", "red", "green", "yellow", "blue", "magenta", "cyan", "white": These options set the foreground color of the output to the corresponding color. For example, "green" will display text in green.

- "brightblack", "brightred", "brightgreen", "brightyellow", "brightblue", "brightmagenta", "brightcyan", "brightwhite": These options set the foreground color of the output to the corresponding bright color.

- "bold", "dim", "italic", "underline", "strikethrough": These options modify the text style of the output. For example, "bold" will make the text bold.

You can also customize the background color of the output by prefixing the color option with "bg", like "bgred" or "bgblue".

To use these options, you can add them to the "color.ui" configuration option in your Git configuration file, like so:

```bash
git config --global color.ui auto # To let git decide the colors
git config --global color.branch.current "green bold" # This sets the current branch to have bold green color
git config --global color.diff.old "red bold" # This tells git that an "old" or "deleted" line of code to be denoted in red. This is when you run "git diff"
git config --global color.diff.new "green bold" # This tells git to show the new lines that have been added to be in green
```

You can use the same principal to set other colors in Git. This is useful if you want to customize Git to your liking.

#### Branches, Merging, and Editor

You can customize which branch git should initialize with. Instead of always creating a default branch called `master` or `main` you could change it to your favourite thing.  
You can use this command

```bash
git config --global default.branch gekkowrld
```

Remember that this is only available from git version 2.28 that was introduced in July 2020. You can run `git --version` to see your version.

```bash
git config --global pull.rebase true # This will apply changes to the top of your commit history resulting in a cleaner history
git config --global pull.rebase false # Git will create a merge commit to combine your local changes with remote changes
```

>> This sets the behaviour of what happens when `git pull` is run.

To set an editor to be opened by git when doing git operations like editing git commits and resolving merge conflicts. Here you can set your favourite editor.

```bash
git config --global core.editor "code --wait" # For setting Visual Studio code.
#The --wait flag is needed to make sure that git doesn't close thinking that it is an empty commit instead it waits
git config --global core.editor vim # For setting vim
git config --global core.editor nano # For setting nano
git config --global core.editor emacs # For setting Emacs
```

## Configure Git by editing the .gitconfig file directly

This is a risky way of doing it but way faster. Remember that editing this file makes the settings global.

Check if you have the file by running:

```bash
ls ~/.gitconfig
```

If there is none, create one. If you have it, open it in your favourite editor.

The first thing we should add to the file is the username and email.

```txt
[user]
	email = gekko_wrld123@email.com 
	username = Gekko Wrld
```

This will add the email and username. Remember if you are using a private email. Use it instead of your actual email.

Now I will add other configurations that are not mandatory

```txt
[init]
	defaultBranch = gekkowrld
[core]
	editor = vim
[color]
	ui = auto
```

`defaultBranch = gekkowrld` will set the default branch to be called `gekkowrld` if `git init` is run. `editor = vim` sets the default editor opened by git to be `vim` and `ui = auto` tells git to pick any color to display it's messages.


## Wrapping up

That is just the tip of the iceberg in configuring git. You can [check out this gist](https://gist.github.com/pksunkara/988716#file-config) to see other options to be added in a `.gitconfig` file. Or you can read the [progit](https://github.com/progit/progit2) book to get even more cool features of git.

Git is a powerful tool that is also flexible. You can customize it as you want to.

If you have any questions or concerns, open an issue [here](https://github.com/codetrybe/git-and-github/issues) and you'll get help.
