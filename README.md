# Mr Scratch
## Description
Mr Scratch allows flexible management of temporary files and notes from your shell.

Perhaps you work on a shared environment where you're sharing space with other users, and you want to ensure unimportant files don't clog up shared space.

Or perhaps you want an area on your own hard drive where you can put short-term downloads or temporary files and know they won't hang around forever taking up your precious disk space.

Enter Mr Scratch, which provides you with a special scratch directory where untouched files will be automagically purged after two weeks (or any time period you choose).

As a bonus, Mr Scratch supplies a daily scratch pad for you to jot down thoughts, code fragments or whatever you choose in a daily "page" from the convenience of your shell. You can then output the last 14 days of your scratch pad to your system pager, making it easy to search for something you've written down recently.

## Setup
To install, place the `mr_scratch` executable in your path, and run `mr_scratch setup`. The script will prompt you for information (you can just hit return to accept the defaults) and direct you on how to complete the setup.

```
$ mr_scratch setup

##################################################
###                                            ###
###              MR SCRATCH SETUP              ###
###                                            ###
##################################################

We're going to set up the following:

* The location of your scratch directory
* How long files are kept before they're purged
* Some command aliases for the scratchpad
* A crontab to purge files past their keep-by date

Please answer the following questions, and take
any manual steps you are prompted for.

Good luck :)

##################################################

Please choose a directory path for your scratch directory (defaults to /Users/heliomass/scratch) :
Please choose the expiry time for files in the scratch directory (in days, defaults to 14) :

The following settings will be applied:
   Scratch directory:    /Users/heliomass/scratch (this directory will be created)
   File expiry:          14 days

The following crontab will need to be added to your setup:
   05 * * * * /bin/bash -c 'source ~/.scratch_config; mr_scratch purge' > /dev/null 2>&1

WARNING: These changes will overwrite your existing settings!

Proceed? (y/N) : y
##################################################

Congratulations! The setup process has completed.

You'll need to take a few final steps before
you're up and running:

1) Please add the following line to your .bashrc,
.profile or .zshrc:

   source ~/.scratch_config

2) Please manually add the following to your crontab
to purge files older than 14 days:

   05 * * * * /bin/bash -c 'source ~/.scratch_config; mr_scratch purge > /dev/null 2>&1'

(note: if you don't know how to install a crontab,
have a look here:
https://help.ubuntu.com/community/CronHowto

3) Restart your shell so you pick up the new
settings

##################################################
```

## Usage
To visit your scratch directory, simply type `scratch`.

To open up your scratch pad for today, type `scratchpad` (note: you will need Vim installed)

To output the complete history of your scratch pad, just type `scratchdump`. The most recent days' content will appear at the top using your system pager (usually `less`) to display the content, making it easy to search through.

If you want to use the path to your scratch directory in your own scripts or aliases, it's kept in `$SCRATCH_DIR`.

If you want to change your settings, you can just run `mr_scratch setup` again.
