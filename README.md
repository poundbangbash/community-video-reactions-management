# Video Reaction Management for macOS 14+
Sonoma introduced video reactions to video calls, on by default.  This payload sets app gestures off by default, per app.

If you notice an app has Video settings but not in this file (the green "Facetime" icon appears in the menu bar when the camera is accessed by the app), please contribute to benefit others that may have that application as well.

To contribute:
1) Run `sudo plutil -p /Users/[username]/Library/Group\ Containers/group.com.apple.secure-control-center-preferences/Library/Preferences/group.com.apple.secure-control-center-preferences.av.plist | grep -i reactions-enabled` to see which apps have reactions enabled. You can also run with `grep -i gestures-enabled` to see if any apps have that key set.
2) Extract the app entry (e.g. `videoeffects/us-zoom-xos/reactions-enabled`)
3) Fork this repo, update the mobileconfig adding the appropriate line(s) and a boolean key of `false`.
4) PR it back.  In the PR make sure to list what the application is in case it's not clear in the mobileconfig setting.

   
