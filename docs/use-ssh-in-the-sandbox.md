# How to use SSH in the sandbox

## What is SSH

> > SSH (Secure Shell) is a network protocol used to securely connect and communicate with remote computers over an unsecured network. It provides a secure encrypted communication channel between two untrusted hosts over an insecure network. SSH is widely used by system administrators, developers, and power users to remotely manage and access their systems and data.
> > SSH uses a client-server model, where the client establishes a secure connection to the server and can then send and receive data through that connection. The server typically runs an SSH daemon, which listens for incoming connections on a specific TCP/IP port. The client must have an SSH client software installed on their local computer to initiate the connection.
> > Once the connection is established, the user can perform various tasks such as executing remote commands, transferring files, and tunneling other network protocols through the secure connection. SSH is widely considered to be a more secure alternative to traditional remote login protocols like Telnet, which transmit data in clear text over the network.

For our case the remote computer or server is [github.com](https://github.com/) and the client is **us**.

## How to configure SSH in the sandbox

**Note**: **Make sure that you have already configured git before proceeding.**

### Configure Git

You can configure git using the following commands:

Make sure that you don't include the quotes unless your name has spaces. If you opted to use a private email use it instead of your actual one.

```bash
git config --global user.name "Your Name" # For your name [only include the quotes if you are using more than one name/word]
git config --global user.email "Your Email" # For email (use the generated if you opted for private email it will look something like this "123456789+gekkowrld@users.noreply.github.com") [Don't include the quotes]
```

Verify if your details are correct by using the following commands

```bash
git config --get user.name # To check your username
git config --get user.email # To check your email
```

Now let's get to configuring SSH.

### Create an SSH

First let's see if we have SSH key in our machine

```bash
ls ~/.ssh/id_ed25519.pub
```

We'll use ED25519 because of its security and speed advantages. You can read more about it [here](https://ed25519.cr.yp.to/)

If the message from the above command is `No such file or directory` then we have to create a new one, if it is there then you can skip this part.

**NOTE**:

> > > If you already have an ssh key in your machine, and it is being used, don't overwrite it. Instead, give a different path in the ssh folder so as to avoid conflicts.

Use the following command to generate a new SSH key

```bash
ssh-keygen -t ed25519 -C "Your email"
```

> > -   If it prompts you for a location to save just press `Enter`
> > -   Next, it will prompt you for a password. You can choose to enter one or not, it is not mandatory

Now let's copy the contents of the file so that we can store them in Github. This will tell Github who we are and remove the need to reauthenticate every time we have to push our code to Github.

```ls
cat ~/.ssh/id_ed25519.pub
```

### Link Your SSH to Github

Make sure you are logged in to Github before continuing with the following steps.

First, you’ll navigate to where GitHub receives our SSH key. Click on your profile picture in the top right corner. Then, click on Settings in the drop-down menu.

Next, on the left-hand side, click SSH and GPG keys. Then, click the green button in the top right corner that says New SSH Key. Name your key something that is descriptive enough for you to remember where it came from.

Now paste the contents of the `cat ~/.ssh/id_ed25519.pub` command that we performed earlier into the key field. The contents should end with your email address.

Click on `Add SSH key` and voila! you are done!

### Testing your key

Follow the [instructions here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection) to test if your key was successfully added to Github
