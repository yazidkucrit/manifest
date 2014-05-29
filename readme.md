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
