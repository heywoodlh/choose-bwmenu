# Bitwarden Choose Menu

This is a work in progress to get the Bitwarden cli functionality in an easy Choose menu.
On selecting an entry, the password is copied to your clipboard for 15 seconds.
During those 15 seconds, a notification is shown indicating which password you
are copying at that time.

## Prerequisites:

Install dependencies:

```bash
brew install bitwarden-cli jq
brew cask install choose-gui
```

Make sure you are already logged in via Bitwarden's CLI:

```bash
bw login
```

## Usage

You can either execute the script from a terminal or by binding it to a key
combination in your window manager.

```
bwmenu 0.4.2

Usage:
  bwmenu [options] -- [rofi options]

Options:
  --help
      Show this help text and exit.

  --version
      Show version information and exit.

  --auto-lock <SECONDS>
      Automatically lock the Vault <SECONDS> seconds after last unlock.
      Use 0 to lock immediatly.
      Use -1 to disable.
      Default: 900 (15 minutes)

  -c <SECONDS>, --clear <SECONDS>, --clear=<SECONDS>
      Clear password from clipboard after this many seconds.
      Defaults: 15 seconds.

  -C, --no-clear
      Don't automatically clear the password from the clipboard. This disables
      the default --clear option.

  --show-password
      Show the first 4 characters of the copied password in the notification.

Examples:
  # Default options work well
  bwmenu
```

## Troubleshooting

The `choose-bwmenu` script uses a MacOS keychain to store and retrieve the necessary authentication token to work with `bw`. Delete it with this command if you suspect something is wrong with the keychain:

```
security delete-keychain bitwarden_choose
```
