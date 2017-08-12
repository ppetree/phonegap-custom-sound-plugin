# phonegap-custom-sound-plugin
Demonstrates how to add custom sound and/or image files to a phonegap project using a plugin

This plugin was originally created to add custom sound files to the Intel XDK build system which has now been retired (shame too).

To use:

1) Add your sound file to the \snd folder. To play cross platforms, sound files should be 16bit .wav files.

2) Edit the plugin.xml file and change the source and target references.

In my case I used these to add custom push notification sounds that would be played with the phonegap-plugin-push plugin and then send notifications via Google Cloud Messaging (now Firebase).

The push notification had some differences in the actual push package that varied greatly from the phonegap-plugin-push documentation. The iOS packet is required to have the file extention while the android would not work with it.  Also, inside the push packet, the way the sound files are referenced is diffent: under apple, the sound file is referenced in "sound" while for Android it is "soundname."

So the push package looked like this on Android:
$androidpacket['soundname'] = "demo";

And on iOS it looked like this:
$applepacket['sound'] = "demo.wav";

