# Video Reaction Management for macOS 14+

## About

macOS Sonoma introduced video Reactions for apps using the camera, which is enabled by default on every app.  This configuration profile disables Reactions by default on a per-app basis.

## Behavior

> [!IMPORTANT]
> **NOTE: THIS CONFIGURATION PROFILE ONLY APPLIES SETTINGS WHEN THE USER LOGS IN**

* If a user is currently logged in when the profile is delivered, no changes are made to any app settings.
* If a user logs out and logs back in, the settings are applied.
* If a user turns on Reactions for an application in the management scope, Reactions will stay on during that login session.  If a user logs out and logs back in, the settings are re-applied (e.g. if you turn on gestures for Zoom, log out and back in, Zoom Reactions are off again).

## Contributing

If you notice an app uses the camera but is not present in this file, please contribute to benefit others who may have that application as well.

1) Launch the target app on your Mac, activate the camera, click the Video button <img src="macos-video-button.png" alt="macOS Video button icon, depicting a green rectangle with a white camera icon in the middle, similar to the FaceTime app icon." height="15" /> in the menu bar, then disable Reactions for that app (see [Use Reactions, Presenter Overlay, and other effects when videoconferencing on Mac](https://support.apple.com/en-us/105117)).
2) Run `sudo plutil -p ~/Library/Group\ Containers/group.com.apple.secure-control-center-preferences/Library/Preferences/group.com.apple.secure-control-center-preferences.av.plist | grep -i reactions-enabled` to see which apps have Reactions enabled. You can also run with `grep -i gestures-enabled` to see if any apps have that key set. *NOTE: The command needs to be run with `sudo` since the plist is readable only by root.*
3) Extract the app entry (e.g. `videoeffects/us-zoom-xos/reactions-enabled`).
4) Fork this repo and update the mobileconfig, adding the appropriate line(s) and a boolean key of `false`. Note that you will need to add keys for both `gestures-enabled` and `reactions-enabled` for each application.
5) PR it back.  In the PR, make sure to list what application has been added, in case it's not clear in the mobileconfig setting.
