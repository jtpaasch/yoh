YOH
===

Yoh is a command line tool that lets you create and build Yesod websites on a (vagrant) VM. So, you create a (vagrant) VM, you install your Yesod website on that VM, and you run/develop your website on that VM too. It all happens on the VM. Yoh is really just a wrapper that makes it easier to do all of this on the VM.


Requirements
------------

The following must be installed/operational:

* A linux/unix/OS X system.
* Git
* Virtualbox 4.3+
* Vagrant 1.4+
* A heroku account (you'll need your username and password)


Installation
------------

To install `yoh`, simply clone the repo (or download and unzip the zip file), then `cd` into the repo folder and type:

    $ ./install

It might ask for your password. Please supply it if asked.


Creating a folder for the VM
----------------------------

The first thing to do is create a folder to house the VM. For instance, you might create a folder called `myproject-vm` in your home folder:

    $ mkdir ~/myproject-vm

The VM and all of its contents will be stored in this folder. If you ever want to seriously purge your system of your Yeseod project, you can just delete this folder and then restart your computer. 


Initializing the VM folder
--------------------------

Once you've created a folder to house the VM, you need to initialize everything. This is done with the `init` command. So, `cd` into your VM folder, then run the `yoh init` command:

    $ cd ~/myproject-vm 
    $ yoh init

That will ready the `myproject-vm` folder for use. Specifically, this command will generate config files for the VM. It won't install the VM itself. It's just config files that get created here.


Deleting the VM
---------------

In a moment, I'll tell you how to create a VM, but if every thing goes bad, it's important to delete it. To do that, you can just run the command:

   $ yoh destroy

If it asks if you want to delete the VM, do say yes. It's also a good idea to delete the whole `myproject-vm` folder, and then to restart your computer. 


Booting up the VM for the first time
------------------------------------

After you've run `yoh init` in the VM folder, you can then boot up the VM. To do that, run the `yoh up` command from the same folder:

    $ yoh up

The first time you run this command, it will take a long time. It will download the VM, boot it up, and then install Haskell and Yesod on the VM.

A few things to note:
* If it says `[default] Available bridged network interfaces:`, just type `1` and hit `Enter`. That simply tells the VM to use the first internet connection available.
* It will take a very long time to boot up your VM and install Haskell and Yesod for the first time. DO NOT let your computer go to sleep or turn off the screen while this happens. This can cause the installation process to hang. 
** If you see any errors with your first `yoh up`, just delete the whole `myproject-vm` folder, restart your computer, and try again --- but be sure your computer never goes to sleep during the process. 

Once `yoh up` is complete, you should then have a VM that is up and running, and it has Haskell and Yesod installed it. It's ready to go.


Booting up the VM later times
-----------------------------

As noted above, the first time you run `yoh up`, it will likely take forever to complete, because it needs to install everything.

The next time you boot it up with `yoh up`, it should only take a few minutes, because this time around it doesn't need to install anything.

The only thing that might happen when you boot up subsequently is that it might aske you for `[default] Available bridged network interfaces:`, in which case you should again just type `1` and hit `Enter`. 


Creating a Yesod Website
------------------------

At this point, you have a VM that has Haskell and Yesod installed on it, but there is no website/project on it. To create that, we can use the `yoh create <projectname>` command, where `<projectname>` can be whatever you want to name your project. The only restriction is that it must be lowercase letters, numbers, or dashes. No spaces or special characters. Just a-z, 0-9, and a dash. 

So, for instance, let's create a project called `test1`:

    $ yoh create test1

This too will take a while, because Yesod has to install a bunch of packages and libraries for your new site. 

When all is said and done...
