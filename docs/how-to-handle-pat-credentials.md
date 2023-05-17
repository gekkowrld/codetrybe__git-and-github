# How to avoid password authentication issues when using PAT

## What is PAT(Personal Access Token)

This is a form of authenticating that are strings of characters that are used to authenticate a user according to [Wikipedia](https://en.wikipedia.org/wiki/Personal_access_token). This is an alternative to a password method where the user decides which password to enter in which some cases the password is weak.

In our case we'll be using Github as the remote computer and Git as our version control.

## How to troubleshoot some some authentication issues

We will go over some of the methods and have a deep dive into a few methods that can be useful.

### Ensure that your password and username are correct

This may seem obvious but many times you may find that you have the wrong spelling of a credentials or you used the wrong ones. First check to see if the credentials you have used are the correct ones. If they are then you can check other troubleshooting methods.

### Verify that you are connected to a stable internet

Some times the issue might be the network not the credentials themselves. Make sure to troubleshoot the network according to your Operating system, computer manufacturer and internet provider.

### Disable Firewalls and Antiviruses

Sometimes there can be some issues because the firewall and or the antivirus blocked the packets from being sent. Disable the firewall and or the antivirus and see if this resolves the issue. If this resolves it, then consider adjusting the settings so that Github can be a trusted domain.

### Store Git credentials somewhere for Git to use for future tasks

Sometimes it is tiresome to retype the credentials until we make an error in typing in the correct ones. So you can let Git handle the authentication by telling it where to find them. This is explained [here](#store-the-credentials-using-a-custom-credentials-helper)

## How do I use PAT to authenticate

There are several ways to authenticate using PAT. Some of the methods are:

1. Copy paste the token as the password when prompted for it.
2. Store it in a .git-credentials file
3. Use custom credentials helper

We'll go over the third options for now. The first option is common so I won't go over it and the second one is not recommended but doable.

## Store the credentials using a custom credentials helper

Before we go start we need to edit some files so that we don't end up repeating the same actions over and over again.  
First open the `.gitconfig` file using any editor of your choice. For me I'll use vi.

```bash
vi ~/.gitconfig
```

Now let's add this line to our file at the end of our `.gitconfig` file:

```bash
[credential "https://github.com"]
	username = gekkowrld # Replace the gekkowrld with your github username
```

Now our file should look something like this:

```bash
[user]
	email = gekkowrd_123@email.com
	name = Gekko Wrld
[credential "https://github.com"]
	username = gekkowrld
```

Note that file content can be different depending on the configurations. Here I have done only the bare minimum configurations.

Now that we have set our username we may start setting up the custom helpers.

First we must have our PAT token string. If you don't have one you can generate one using [this instructions](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

Now go tour terminal and clone the repository that you would like to make changes to using the PAT into your local computer or the sandbox.

For me I'll clone the repository called `test-ground` to my local computer.

```bash
git clone https://ghp_eLhVuAdHDFRAUKDnWlICmtl46G4I983NylLs:gekkowrld@github.com/gekkowrld/test-ground.git
```

Make a changes you want to the repository, then add them to the staging area and then commit them.

```bash
git add . # To add all the changes
git commit -m "I made my change" # Commit your changes along with a descriptive message
```

Now we do enter the most important command in this article:

```bash
git config credential.helper store # Nothing will be printed in the stdout
```

Then we push our commits to Github

```bash
git push https://github.com/gekkowrld/test-ground.git # Make sure it is that you enter the complete url as I have done here.
Substitute https://github.com/gekkowrld/test-ground.git with the url of your repo
```

Git will prompt you to enter the password which will be your token. Copy the token and paste it in. No visible sign will be shown when entering the password but just press `Enter`. Your changes will be pushed to Github safely.

From now on until your token expires, Git will not ask you for your password or username for the particular repository. You can do this with other repositories if you want to.

Do keep in mind that the password is stored in plain text in your local computer. You can see how it is stored by entering the following command:

```bash
cat ~/.git-credentials
```

The file will look something like this:

```txt
https://gekkowrld:ghp_eLhVuAdHDFRAUKDnWlICmtl46G4I983NylLs@github.com
```

There is another way to store the credentials like caching and using third party options.

For caching, this will not store the credentials in the hard disk. Every time your machine restarts, the credentials are erased too. This is a better way if you want security.

To do this you do all the steps except where we used the command `git config credential.helper store` you use `git config credential.helper cache`.

Now if you want to remove the credentials for any reason you can run this command to remove them:

```bash
git config --unset credentials.helper # To remove the saved credentials from the disk
# or
git credential-cache exit # To remove the cached memory before time-out
```

To learn more about [gitcredntials](https://git-scm.com/docs/gitcredentials) you can go to <https://git-scm.com/docs/gitcredentials> or about [caches at](https://git-scm.com/docs/git-credential-cache) <https://git-scm.com/docs/git-credential-cache>

## Conclusion

This method will surely help you not get some weird long strings of text telling you that you have entered the wrong username or password. There are other methods like using an [ssh](https://codetrybe.github.io/git-and-github/use-ssh-in-the-sandbox) that can be used as alternatives.
