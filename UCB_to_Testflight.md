# The Path From Unity Cloud Build To Testflight

## The Problem

I don't have a Mac, and Apple really wants you to have one in order to make iOS apps.

I borrowed a friend's Mac, which sufficed for generating certificates and getting provisioning profiles set up and all that.

But where it fails is...surprisingly...uploading to Testflight (App Store Connect)!

For some strange reason this requires a recent enough Mac to run one of several tools. Though Apple's docs say you can do this with a Windows version of iTMSTransporter (see https://help.apple.com/itc/transporteruserguide/#/apdAbeb95d60 ), this still requires XCode to generate an AppStoreInfo.plist at least once.

## The Solution

While I got close to having a workaround for uploading from PC, what I discovered was a much better solution: a way to automatically upload to Testflight directly from Unity Cloud Build using a script as a post-build hook.

https://forum.unity.com/threads/path-to-the-final-ipa-file.754331/#post-5528596

This link lands you smack in the middle of a pretty long forum thread, but you're in the vicinity of instructions to make a bash script, stash it in the Assets/Editor directory of your project, and set up a few Environment Variables for your build target name (TARGET_NAME) and your App Store Connect credentials (ITUNES_USERNAME, ITUNES_PASSWORD -- you should follow the instructions to generate a single-use password and use it specifically for this).

Amazingly this worked on the first try!

Except Apple is now complaining about UIWebView even though I don't use it in my project...

--BCM 2020/12/01