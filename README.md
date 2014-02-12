YOH
===

Yoh is a command line tool that lets you create and build Yesod websites on a VM. It can deploy sites to heroku too. Everything is done with a few simple commands. 

Want to create a VM in your current folder? Type:

    yoh init
    
Want to boot up the VM? Type:

    yoh up
    
Want to create a Yesod website? Type:

    yoh create mysite
    
Want to run that site and see it at http://localhost:3000? Type:

    yoh run mysite
    
Want to make your site a heroku site? Type:

    yoh herokufy mysite

Want to deploy it to heroku? Type:

    yoh deploy heroku mysite

That's it. 


Requirements
------------

Yoh is written in python, which any linux/unix/OS X system should have. Apart from that, you just need virtualbox and vagrant:

* Virtualbox 4.3+
* Vagrant 1.4+

If you want to deploy to heroku, you'll need a heroku account too.


Installation
------------

To install `yoh`, clone the repo (or download and unzip the zip file), then `cd` into the repo folder and type:

    $ ./install

It might ask for your password. Please supply it if asked.


Creating a folder for the VM
----------------------------

The first thing to do is create a folder to house the VM. For instance, you might create a folder called `myproject-vm` in your home folder:

    $ mkdir ~/myproject-vm

The VM and all of its contents will be stored in this folder. If you ever want to seriously purge your system of your Yeseod project, you can just delete this folder. 


Initializing the VM folder
--------------------------

Once you've created a folder to house the VM, you need to initialize everything. This is done with the `init` command:

    $ cd ~/myproject-vm 
    $ yoh init

That will ready the `myproject-vm` folder for use. Specifically, this command will generate config files for the VM. It won't install the VM itself. It's just config files that get created here.


Booting up the VM
-----------------

After you've run `yoh init` in the VM folder, you can boot it up. To do that, run the `yoh up` command from the same folder:

    $ yoh up

The first time you run this command, it will take a long time. It will download the VM, boot it up, and then install Haskell and Yesod on the VM. After the first time though, the VM will boot up quickly.

A few things to note:
* If it says `[default] Available bridged network interfaces:`, just type `1` and hit `Enter`. That simply tells the VM to use the first internet connection available.
* It will take a very long time to boot up your VM and install Haskell and Yesod for the first time. DO NOT let your computer go to sleep or turn off the screen while this happens. This will generate errors, and you'll have to delete the VM folder, restart your computer, and start all over. 

Once `yoh up` is complete, you should then have a VM that is up and running, and it has Haskell and Yesod installed it. It's ready to go.


Creating a Yesod Website
------------------------

At this point, you have a VM that has Haskell and Yesod installed on it, but there is no website/project on it. To create that, we can use the `yoh create <site>` command, where `<site>` can be whatever you want to name your project. The only restriction is that it must be lowercase letters, numbers, or dashes. No spaces or special characters. Just a-z, 0-9, and a dash.

So, for instance, let's create a project called `test1`:

    $ yoh create test1

This too will take a while, because Yesod has to install a bunch of packages and libraries for your new site. 


Running the website
-------------------

To run the site on Yesod's development server, use `yoh run <site>`, for instance:

    $ yoh run test1

Then you can see your site at localhost:3000. To stop the development server, just hit Enter.


Deploy to heroku
----------------

If you want to deploy your Yesod site to heroku, first make it heroku-ready with the `yoh herokufy <site>` command:

    $ yoh herokufy test1
    
This will generate all the files that heroku requires before you deploy anything to them.

Once you've herokufied your site, you can deploy it live with `yoh deploy heroku <site>`:

    $ yoh deploy heroku test1
    
When that finishes, you can visit your site at the URL it spits out on the screen.
