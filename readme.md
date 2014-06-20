<<<<<<< HEAD
Paranoid SaberDroid
===================
SaberMod GCC Optimized AOSPA with a Twist
-----------------------------------------

This is unofficical Paranoid Android by [Team AOSPAL](http://google.com/+AospalOrg)
-----------------------------------------------------------------------------------


[Official PA Source Is Here](https://github.com/AOSPA)
------------------------------------------------------

Building
--------

Refer to this link:

    https://github.com/AOSPAL/manifest/wiki/How-to-build-Paranoid-Saber-Droid


Submitting Patches
------------------

Paranoid SaberDroid is open source, send your patches from your local source:

    cd <working_directory>
    repo start <branch> AOSPAL/<repo>
    cd <repo>
    git add -A
    git commit -a
    cd <working_directory>
    repo upload AOSPAL/<repo>

Commit your patches in a single commit. Squash multiple commits using this command:

    git rebase -i HEAD~<# of commits>


Sync Errors
-----------

When met with sync errors:

    repo sync -j1

Take note of troublesome repositories. For example, if you get fetch errors on "android_frameworks_base", you can simply git clone it by doing the following:

    git clone https://github.com/AOSPAL/android_frameworks_base <branch>

When met with build errors:

    Use the error to read the error. In other words, most of the time the build error
    will tell you what the problem is. For example, "no rule to make target", means that
    there could be a missing or malformed line in the Makefile (Android.mk) of that
    particular directory.

Log your builds by amending the following to your build command:

    2>&1 | tee build.log

This will create a file in your source's root directory called "build.log". You can share this via Pastebin
to your favorite XDA thread.

Google! Google! Google! Nine times out of ten, the error you're experiencing has been experienced by someone
else. Make sure to check the interwebz for your issue! XDA is also a great place to find help!
=======
# ParanoidAndroid #

## Working on translations ##

We're using [Crowdin](https://crowdin.net/project/aospa-framework) to accept translations so you
should join it if you are interested in working on translating a part of the project.

## Grabbing the source ##

[Repo](http://source.android.com/source/developing.html) is a tool provided by Google that
simplifies using [Git](http://git-scm.com/book) in the context of the Android source.

### Installing Repo ###

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/bin
$ PATH=~/bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

# Make Repo executable
$ chmod a+x ~/bin/repo
```

### Initializing Repo ###

```bash
# Create a directory for the source files
# This can be located anywhere (as long as the fs is case-sensitive)
$ mkdir WORKSPACE
$ cd WORKSPACE

# Install Repo in the created directory
# Use a real name/email combination, if you intend to submit patches
$ repo init -u https://github.com/AOSPA/manifest -b kitkat
```

### Downloading the source tree ###

This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let Repo take care of all the hard work
$ repo sync
```

## Building ##

The bundled builder tool `./rom-build.sh` handles all the building steps for the specified device
automatically. As the device value, you just feed it with the device codename (for example,
'hammerhead' for the Nexus 5).

```bash
# Go to the root of the source tree...
$ cd WORKSPACE
# ...and run the builder tool.
$ ./rom-build.sh DEVICE
```

## Submitting Patches ##

We're open source and patches are always welcome!

You can see the status of all patches at [Gerrit Code Review](https://gerrit.paranoidandroid.co/).

### Following the standard workflow ###

```bash
# Start by going to the root of the source tree
$ cd WORKSPACE

# Create a new branch on the specific project you are going to work on
# For example, `repo start fix-clock AOSPA/android_frameworks_base`
$ repo start BRANCH AOSPA/PROJECT

# Go inside the project you are working on
$ cd PROJECT

# Make your changes
...

# Commit all your changes
$ git add -A
$ git commit -a

# Upload your changes
$ cd WORKSPACE
$ repo upload AOSPA/PROJECT
```

### Making additional changes ###

If you are going to make more changes, you just have to repeat the steps (except for `repo start`
which you should not repeat) while using `git commit --amend` instead of `git commit -a` so that
you avoid having multiple commits for this single change. Gerrit will then recognize these changes
as a new patch set and figure out everything for you when you upload.

### Squashing multiple commits ###

Your patches should be single commits. If you have multiple commits laying around, squash them by
running `git rebase -i HEAD~<commit-count>` before uploading.

### Writing good commit messages ###

You will be asked a commit message when you run `git commit`. Writing a good commit message is
often hard, but it is also essential as these messages will stay around with your changes and
will be seen by others when looking back at the project history.

A few general pointers to keep in mind when writing the commit message are that you should use
imperative as it matches the style used by the `git merge` and `git revert` commands (that means
"Fix bug" is preferred over "Fixes bug", "Fixed bug" and others) and that you should write the
first line of the commit message as a summary of the commit. It should always be capitalized and
followed by an empty line. You might optionally include the project name at the start and try to
keep it to 50 characters when possible as it is used in various logs, including "one line" logs.
>>>>>>> PA/kitkat
