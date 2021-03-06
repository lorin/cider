[![PyPi version](https://pypip.in/version/cider/badge.svg)](https://pypi.python.org/pypi/cider/)
[![PyPi downloads](https://pypip.in/status/cider/badge.svg)](https://pypi.python.org/pypi/cider/)
[![PyPi status](https://pypip.in/download/cider/badge.svg)](https://pypi.python.org/pypi/cider/)

## Start with a clean slate

Cider is a simple wrapper for [Homebrew](http://brew.sh) and [Homebrew Cask](http://caskroom.io) that allows you to save your setup across different machines. This lets you to restore a backup without having to deal with the mess that was the state of your previous installation, or painstakingly babysit the process step-by-step.

Simply run the following on a new machine:

    git clone [YOUR_REPO] ~/.cider
    cider restore


... and you’ll be back up and running, with all of your applications and command line utilities re-installed (and configurations restored).


In addition to Homebrew, Cider also supports managing your user defaults, restoring symlinks, and running scripts to conveniently manage other settings such as your dotfiles.


## Installation

Cider is available directly from [PyPI](https://pypi.python.org/pypi/cider):

    pip install cider


## Configuration

All configuration files are stored in the `~/.cider` directory as JSON. E.g., here’s an example bootstrap file:

    {
        "after-scripts": [
            "brew linkapps"
        ],
        "casks": [
            "adobe-creative-cloud",
            "dropbox",
            "firefox",
            "flash",
            "flux",
            "github",
            "google-chrome",
            "google-hangouts",
            "heroku-toolbelt",
            "iterm2",
            "mplayerx",
            "sublime-text",
            "transmission",
        ],
        "formulas": [
            "brew-cask",
            "emacs",
            "fish",
            "git",
            "go",
            "macvim --overwrite-system-vi",
            "python",
            "python3",
            "xctool"
        ],
		"icons": {
			"iTerm": "https://dribbble.com/shots/1702947-iTerm-Replacement-Icon/attachments/271548"
		},
		"symlinks": {
			"bash/.*": "~",
			"bin/*": "~/bin/",
			"git/.*": "~",
			"sh/.*": "~",
			"vim/.*": "~"
		},
        "taps": [
            "caskroom/cask"
        ]
    }

User defaults are stored similarly:

    {
        "NSGlobalDomain": {
            "ApplePressAndHoldEnabled": false
        }, 
        "com.apple.dock": {
            "tilesize": 48
        }, 
        "com.iconfactor.mac.xScope": {
            "generalShowDockIcon": false
        }
    }

To see how this works out in practice, feel free to take a look at [my dotfiles](https://github.com/msanders/dotfiles).

## Backup your existing setup

To save the state of your existing setup:

    mkdir ~/.cider
    touch ~/.cider/bootstrap.json
    cider missing
    cider cask missing

## Caveats

There doesn't seem to be a way to re-install purchases made from Mac App Store via the command line just yet, so those have to be done by hand.

**Note**: Cider is a work-in-progress, but it’s fairly well-tested and should be kind to your machine.
