# Lid Hibernate — downloads

Releases only. No source code here: the source lives in a private repository.

## What it is

A small Windows tray application that hibernates the laptop a configurable time
after the lid is closed, by running `shutdown /h`. This is useful on a PC where
sleep is blocked by policy but hibernation works.

- Waits N seconds after the lid closes (default 30), then hibernates. Reopening
  the lid cancels it.
- Ignores lid close while an external monitor is in use. If that monitor is
  disconnected while the lid stays closed, the countdown starts at that moment.
- Optional start with Windows (per-user, no administrator rights).
- Self-updating from this repository; downloads are SHA-256 verified.

## Install

Every release publishes two packages with the same program:

- **`LidHibernate-Windows-light.zip`** (~130 KB) — framework-dependent, needs the
  .NET 8 Desktop Runtime. This is what the automatic updater installs.
- **`LidHibernate-Windows.zip`** (~63 MB) — self-contained, nothing to install.
  Use it when the .NET 8 Desktop Runtime is not available.

Unzip it anywhere permanent (not Downloads), run `LidHibernate.exe`, and
right-click the tray icon. SmartScreen warns on the first run because the exe is
unsigned: choose **More info → Run anyway**.

Before relying on it, check that closing the lid does not sleep the PC:
`powercfg /q SCHEME_CURRENT SUB_BUTTONS LIDACTION` should report
`0x00000000` (Do nothing).

## Updates

Every release publishes `LidHibernate-version.json` next to the zips. The
application reads it, compares versions, downloads the matching build and
verifies its SHA-256 before installing it. From the first release on, updates
are handled by the app: **Check for updates** and **Install update** are
in the tray menu, and **Auto-update** is on by default.

Release notes: see the Releases page.
