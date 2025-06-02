# Silent Chrome - Silently Install Web Store Extensions on Google Chrome on MacOS

Author: AsaurusRex

## Purpose

This is a project showcasing hows how to silently install Web Store extensions on Google Chrome on MacOS. See the blog posts on silently installing Web Store Extensions: <https://medium.com/@marcusthebrody/silently-install-chrome-extensions-macos-version-becf164679c2> (for Part 1) and <https://medium.com/@marcusthebrody/silently-install-macos-chrome-extensions-part-2-c9deab4216cd> (for Part 2)

## Requirements

This code is designed to run with Python3, but you might want to modify it depending on what your target macOS system has.

## Technique

To run this technique:

1. Provide the value for `extension_path` via the `-e` argument and optionally the path to target Chrome profile via the `-p` argument (Defaults to `~/Library/Application Support/Google/Chrome/Default`).

2. Kill the currently running Google Chrome process/processes; e.g. use the command `killall "Google Chrome"`.

3. Run the `silent_chrome.py` script on target before Chrome is launched again. This will write in our entries into the Secure Preferences file, meaning the next time Chrome is loaded the extension will be loaded with developer mode turned on. You can optionally launch this yourself.

    e.g. `python3 silent_chrome.py -e /my/new/extension [-p ~/Library/Application Support/Google/Chrome/Profile 2]`

As we can see, this is much simpler than the previous method. There are no extension repairs required nor multiple killings of Chrome. If you are having issues, you can always copy that first step from before, namely “Download your desired extension on a test/attacker controlled laptop. Navigate to the Secure Preferences file and carve out the desired json blob for your extension” — but make sure to replace first_install_time, last_update_time, and location fields with the values shown in the script.

## Future Works

Abuse existing extensions which will always exist, like Google Hangouts.

Defeat chrome://policies

Write this in something outside of python for easier deployment.

## Credit

Special thanks to Nicholas Murray for providing a lot of the code that makes this happen and getting me interested in this topic in the first place with his blogs.
