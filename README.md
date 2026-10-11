# Atelier

Atelier is a macOS app for working with many Claude Code sessions in parallel: real terminals that stay alive in the
background, session states at a glance, files, changes and review in one window.

This repository only hosts the releases (no source code). Download them from
[Releases](https://github.com/frmusso/atelier-releases/releases).

## Requirements

- A Mac with Apple Silicon (M1 or later) and macOS 13 Ventura or later.
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and signed in (`claude` works in Terminal).

## Install

1. Open the [Releases](https://github.com/frmusso/atelier-releases/releases) page and download
   `Atelier-<version>-arm64.dmg` from the newest release (betas are marked *Pre-release*; during the preview they are
   the only ones).
2. Open the DMG and drag **Atelier** onto **Applications**. Eject the DMG.
3. Open Atelier from Applications. The first time, macOS blocks it ("Apple could not verify…"), because Atelier is not
   notarized by Apple yet. Click **Done**, then:
   - open **System Settings › Privacy & Security**;
   - scroll down to *Security*: next to "Atelier was blocked to protect your Mac" click **Open Anyway**;
   - confirm with your password or Touch ID, then click **Open**.

   You only do this once: updates installed by Atelier itself are not blocked.
4. Open a project folder and start a Claude session with ⌘N. Atelier asks for the microphone only if you turn on
   dictation (Settings › Dictation).

## Updates

Atelier keeps itself up to date:

- it checks for a new version shortly after launch, then every 6 hours; **Atelier › Check for Updates…** (or
  Settings › About › Check Now) checks right away;
- the update is downloaded in the background and verified (Atelier's release signature and code-signing identity)
  before anything is installed;
- when it is ready, the footer shows **Update ready · Restart**: restart whenever you like, your sessions keep running.

Rarely, a version needs Atelier's background service restarted. Then Atelier does not install it on its own: Settings ›
About says so with **Open Release Page**; install that version from its DMG like the first time (this closes the
running sessions).

Atelier can only update itself from the **Applications** folder. If you opened it straight from the DMG or from
Downloads, Settings › About shows "Move Atelier to your Applications folder to get updates" (with **Open
Applications**): drag Atelier there, then open it from Applications. If an update can't be installed, the message
offers **Open Release Page**: download the DMG of the new version and install it like the first time.

### Going back to the previous version

After an update, the version you had is kept for a while as a hidden `.Atelier-previous.app` next to
`/Applications/Atelier.app`; Atelier deletes it the second time the new version starts. If the new version does not
work for you before that:

1. Quit Atelier.
2. In Terminal:
   `mv /Applications/Atelier.app ~/.Trash/Atelier-new.app && mv /Applications/.Atelier-previous.app /Applications/Atelier.app`
3. Open Atelier, set the channel to **Off** in Settings › About (otherwise it updates again), and tell Francesco.

Once the copy is gone, install an older version from its DMG on the
[Releases](https://github.com/frmusso/atelier-releases/releases) page the same way.

### Channels

Choose the channel in **Settings › About**:

- **Auto**: the channel of the version you downloaded (the default);
- **Stable**: tested releases;
- **Beta**: new features first, together with every stable release;
- **Off**: no automatic checks.

## Report a problem

Send Francesco a message with:

- the Atelier version and channel (Settings › About) and your macOS version;
- what you did, what you expected and what happened (a screenshot helps);
- if it looks like a crash or an update problem, the log file
  `~/Library/Application Support/Atelier/logs/app.log` (in Finder: Go › Go to Folder…). It can contain the paths of
  your projects: have a look before sharing it.

## Uninstall

Quit Atelier, close the sessions you still have running, move `/Applications/Atelier.app` to the Trash and, to remove
its data too, the folder `~/Library/Application Support/Atelier`.
