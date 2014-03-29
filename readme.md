Paranoid SaberDroid
===================
SaberMod GCC Optimized AOSPA with a Twist
-----------------------------------------

This is unofficical Paranoid Android by [Team AOSPAL](http://google.com/+AospalOrg)
-----------------------------------------------------------------------------------


[Official PA Source Is Here](https://github.com/AOSPA)
------------------------------------------------------

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

Building
--------

To get started, you'll need to get
familiar with [Git and Repo](http://source.android.com/download/using-repo).

There are four (4) main branches to build from:

1) "kitkat" (Stock vanilla AOSPA, for nexus devices)
2) "kitkat-remix" (our main branch, filled with non-PA features) 
3) "kitkat-legacy" (stock vanilla AOSPA, for non-nexus devices)
4) "remix-legacy" (filled with non-PA features, for non-nexus devices)


Initialize repo:

    repo init -u git://github.com/AOSPAL/manifest.git -b <branch>
    
Sync the repo:

    repo sync -j<# of threads you would like to use>
    
Build (Automated):

    make clean && ./rom-build.sh <device>
    
Build (Manual):

    make clean && . build/envsetup.sh && lunch psd_<device>-userdebug && make -j<# of threads you want> bacon
    

Errors
------

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
