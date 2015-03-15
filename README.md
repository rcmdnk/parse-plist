# parse-plist

Parser of plist in OS X.

## Installation

By install script:

    $ curl -fsSL https://raw.github.com/rcmdnk/parse-plist/install/install.sh |sh

This installs Homebrew if it has not been installed, too.

By Homebrew:

    $ brew install rcmdnk/rcmdnkpac/parse-plist

Or download `bin/parse-plist` and put it in anywhere under `PATH` (e.g. `~/usr/bin/`)

## Usage

By default, `parse-plist` converts all plist to `defaults` commands:

    $ parse-plist
    defaults write "com.adobe.air.ApplicationInstaller" "NSNavLastRootDirectory" -string "~/Applications"
    defaults write "com.adobe.air.ApplicationInstaller" "NSNavPanelExpandedSizeForOpenMode" -string "{1680, 1023}"
    defaults write "com.apple.ActivityMonitor" "OpenMainWindow" -bool False
    defaults write "com.apple.ActivityMonitor" "ShowCategory" -int 100
    ...

You can specify a plist file or a xml file of plist:

    $ parse-plist com.apple.dock
    defaults write "com.apple.dock" "orientation" -string "bottom"
    defaults write "com.apple.dock" "showMissionControlGestureEnabled" -bool True
    defaults write "com.apple.dock" "autohide" -bool True
    ...

JSON output is available, too:

    $ parse-plist com.apple.dock --out json
    {
      "com.apple.dock": {
        "showDesktopGestureEnabled": false,
        "loc": "ja_JP",
        "dashboard-in-overlay": true,
        ...

## HELP

    $ ./bin/parse-plist -h
    usage: parse-plist [-h] [--date] [--data] [--dict] [--array] [--all] [--user]
                       [--system] [-o OUT]

    optional arguments:
      -h, --help         show this help message and exit
      --date             Enable "date" output.
      --data             Enable "data" output.
      --dict             Enable "dict" output.
      --array            Enable "array" output.
      --all              Enable all outputs.
      --user             Check user settings.
      --system           Check system settings.
      -o OUT, --out OUT  Set output format (defaults commands or json format).
                         Default is cmd. Use json/dict/dic for json format. Others
                         for the command list.
