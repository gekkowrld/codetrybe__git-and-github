# How to clone a repository from Github

## What is cloning?

Cloning is the process of creating a replica or duplicate of something. In our case, the replica we want to create is a repository. We'll clone it into our local computers.

There are three main ways to clone repositories from Github:

- Using HTTPS
- Using SSH
- Using Github CLI

We'll explore the three options below.

I'll be using `test-ground` as the repository and `gekkowrld` as the username. Be free to change to the correct username and repository when following along.

If you haven't configured Git yet, refer to this article: [How to configure git](https://codetrybe.github.io/git-and-github/how-to-configure-git)

## Using HTTPS

To provide an example, let's assume my Personal Access Token (PAT) is ghp_eLhVuAdHDFRAUKDnWlICmtl46G4I983NylLs. Remember to use your own PAT instead of the one I provided, as the one I'm using is not valid. I have modified it for security reasons.

This is the easiest and fastest way to clone a repo. It is available if you are either logged in or not. You can see more about this method [here](https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls).

Now let's get into the sweet stuff of cloning.

Cloning using this method can be done in two ways. Both are fine and none is "better" than the other one. However, ALX recommends one over the other. We'll start with the one recommended by ALX then we'll go over the other one.

**IMPORTANT:** Before you continue make sure that you have your PAT ready. If you don't have it you can [follow these steps to get one](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

### Using the recommended method

Now let's clone our repository using the ALX recommended method.  
This is the patter that you should use:

```txt
git clone https://your_PAT@github.com/username/repository.git
```

Now let's clone our `test-ground` repository

```bash
git clone https://ghp_eLhVuAdHDFRAUKDnWlICmtl46G4I983NylLs@github.com/gekkowrld/test-ground.git
```

This will clone the repository to my local computer. We'll make some few changes.

Let's add a file named new_file.txt

```bash
touch new_file.txt
```

Now let's stage the file and commit the changes.

```bash
git add new_file.txt # Add new_file.txt to the staging area
git commit -m "Add new_file.txt" # Commit the file
```

When pushing Git will ask you for your credentials i.e., username and password. Enter your username and your token will be your password. In my case, that'll be `ghp_eLhVuAdHDFRAUKDnWlICmtl46G4I983NylLs`. If you encounter any trouble, you can use this article: [Troubleshooting PAT credentials](https://codetrybe.github.io/git-and-github/how-to-handle-pat-credentials).

### Using the other method

There is another way to do it that doesn't require a complicated pattern to clone.

In this method, we'll just clone the repository by using the link provided by Github.

```txt
git clone https://github.com/gekkowrld/test-ground.git
```

This will clone the repository into our local development environment.

We'll add contents to a file named `new_file.txt`

```bash
echo "We are using HTTPS to clone our repository" >> new_file.txt
```

We'll stage our files and commit them.

```bash
git add new_file.txt # To add the files into the staging area
git commit -m "Add content to new_file.txt" # Commit the file
```

The final step is to push to Github.  
Git will ask us for our username and password. The password is the token that you created in Github. In my case that'll be `ghp_eLhVuAdHDFRAUKDnWlICmtl46G4I983NylLs`

## Using SSH

I have already written an article on how to configure SSH [here](https://codetrybe.github.io/git-and-github/use-ssh-in-the-sandbox). Make sure that you have followed the steps outlined [here](https://codetrybe.github.io/git-and-github/use-ssh-in-the-sandbox) before coming back.  
If the link doesn't work you can copy this link <https://codetrybe.github.io/git-and-github/use-ssh-in-the-sandbox> to your browser or go to [CodeTrybe Github](https://github.com/codetrybe/git-and-github/blob/main/docs/use-ssh-in-the-sandbox.md) to read the markdown file.

After you have finished configuring, now we'll go step by step on how to clone using SSH.

First copy the link that is provided by Github.

```txt
git@github.com:gekkowrld/test-ground.git
```

Now let's clone the repo to our local dev environment

```bash
git clone git@github.com:gekkowrld/test-ground.git
```

Let's add a file named `hello.sh` to our repository

```bash
echo -e "echo \"Hello, World\"" > hello.sh
```

Stage the changes and commit them.

```bash
git add hello.sh
git commit "Add hello.sh file"
```

To push, you'll do it normally.

```shell
git push
```

Git will push the changes to Github without asking for any further authentication. If it asks you for one. Enter the passphrase that you entered during configuration process.

## Github CLI

For configuration, check out the [official installation guide](https://github.com/cli/cli#installation). If you are not sure, use the instructions about Debian or follow this link <https://github.com/cli/cli/blob/trunk/docs/install_linux.md>

To authenticate please refer to the [official article](https://cli.github.com/manual/gh_auth_login)

Alternatively, you can run the script provided at <https://gist.github.com/gekkowrld/c267b9e7480dece7d9192cde92c2f0d1>. Make sure that you have a token that has a minimum of this requirements:

`The minimum required scopes are 'repo', 'read:org', 'admin:public_key'`

Now to clone simply copy the code provided by Github

```txt
gh repo clone gekkowrld/test-ground
```

You can make changes, stage them and commit. It doesn't require a password when you commit the code.

## Conclusion

If any of the command doesn't work or you don't understand something you can open an issue at <https://github.com/codetrybe/git-and-github/issues/new>.

HAPPY CODING!
