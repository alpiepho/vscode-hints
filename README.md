# vscode-hints
Some of my hints for configuring VS Code, like keyboard shortcuts, great plugins, remote editing via ssh, etc.

## Why

After using VS Code for a couple years, I have collected a number of hints and techniques.  I tend to "just rememeber" when using them and setting up new systems.  I recently had some success with remote-SSH that myself and other developers were looking for on a past project.  I thought this would be a good time to explain the solution I found and add a few other hints.

## Plugins


- GitLens — Git supercharged ([Link](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens))
Shows git blame details in line with code.
- Prettier - Code formatter ([Link](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode))
Auto formating for most files.


switch to vi and limits

## Task Bar?
- Markdown Preview
- Format Document

## Keyboard Short Cuts
- command-D multi cursor : lets you edit multiple lines at the same time
- command-/ : toggle line comments for selected lines

## Remote-SSH to Centos6

I have had the need to use VS Code on Centos6 come up twice recently.  Thru a series of VS Coe documents, I think I understand how to do this.

First, the main VS Code article about [remote development])https://code.visualstudio.com/docs/remote/remote-overview) had a good picture of how it works.  The followup article about [remote-SSH](https://code.visualstudio.com/docs/remote/ssh) take this further, explaining how VS Code can use an ssh tunnel to run your IDE on a host system and edit code on the remote system.

Install the remote-ssh extenstion is easy, and adds a green button on the lower left outside edge of the VS Code frame.  
When you try this with a Centos6 based target, it will attempt to load the target side agent and compile it (I think).  At this point you will get an error because the required compilers are not available.

Digging further, I found [this](https://code.visualstudio.com/docs/remote/linux) about linux installation and finally a
page with [Centos6 workraounds](https://code.visualstudio.com/docs/remote/linux#_updating-glibc-and-libstdc-on-rhel-centos-6)

This workaround does add a number of libraries to the target system, and **REQUIRES** sudo acess, but it is working for me.

## How I am using Remote-SSH

Once I established the connection (clicking the green button brings up dialog to set ssh credentials), you are essentially on the remote system.  When you first attach a directory, it will prompt for a ssh password, then the code tree will be the files on the remote directory.  

Any terminal window is an ssh terminal window on that system.

Some of the files I am changing on the remote system have limited permissions.  In that case I can right-click on the file in the directory tree, "copy path", then in a terminal window:

<pre>
sudo chmod 777 <paste from copy path>
</pre>


## Example of Writing a Plugin

TBD - describe experience from publishing rpn-hex-calc


