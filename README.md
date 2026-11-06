# Qrame

Two panels for Premiere Pro. This repository holds no source code, only the signed installer packages.

| Panel | What it does |
|---|---|
| **Qrame** | Re-cuts the active sequence by timecode and joins what is kept into a new, gap-free sequence. The original timeline is never touched. Three ways in: drop in a finished SRT; let Silence Cut measure the pauses and cut them out; or run the automatic pipeline, which transcribes the audio (locally with Whisper, or with Gladia) and lets a model pick the sections to keep from your prompt. It also places captions on the timeline. |
| **Qrame Cont** | Bulk MOGRT parameter editing, per-clip subtitle text editing, batch keyframe easing, and framing tools (QZoom, QPan, QStep). |

## Download

No version has been published yet.

Older versions are on the [Releases](https://github.com/menestopal/Qrame-releases/releases) page. Download only the `.dmg` there;
GitHub adds the "Source code" archives on its own, and they are not needed for installing.

## Installing Qrame 0.1.2 and Qrame Cont 0.2.1

Qrame and Qrame Cont are two panels for Premiere Pro. Installing them takes
about a minute.

Requirements: macOS and Premiere Pro 25.0 or later (tested on 26.3). This
installer does not run on Windows.

### 1. Open the disk image

Double-click `Qrame_0.1.2_Cont_0.2.1.dmg`. A disk called **Qrame 0.1.2 + Cont 0.2.1** opens in Finder:

| | |
|---|---|
| `Install.command` | The installer. This is the one you run. |
| `INSTALL.html` | These instructions. |
| `Qrame_0.1.2.zxp` | The Qrame panel, signed. You don't have to open it yourself. |
| `QrameCont_0.2.1.zxp` | The Qrame Cont panel, signed. You don't have to open it yourself. |
| `Templates` | The caption templates (`.mogrt`) the panels are set up for. |

### 2. Install

Quit Premiere Pro, then double-click `Install.command`. Terminal opens and
reports each step.

The first time, macOS may refuse to open it, saying Apple could not verify it
or that it comes from an unidentified developer. That is expected: the file
comes straight from us, not from the App Store. There are two ways past it:

- Click **Done**. Open **System Settings › Privacy & Security**, scroll down to
  the line about `Install.command` and click **Open Anyway**. Enter your
  password, then click **Open**.
- Or open Terminal (**Applications › Utilities › Terminal**), type `bash `
  (with a space after it), drag `Install.command` into the Terminal window and
  press Return.

The installer writes to these places and nowhere else:

```
~/Library/Application Support/Adobe/CEP/extensions/net.fokusplus.qrame.bundle/       Qrame
~/Library/Application Support/Adobe/CEP/extensions/net.fokusplus.qrame.cont.bundle/  Qrame Cont
~/Library/Application Support/Adobe/Common/Motion Graphics Templates/                the templates
```

The panels are signed, so no developer setting has to be turned on. If another
copy of a panel is already installed somewhere else, the installer stops
without changing anything and prints the command that removes that copy.

When it is done you can eject the disk (the ⏏ next to it in Finder) and delete
the `.dmg`.

### 3. Open the panels

Start Premiere Pro, open a project, and choose **Window › Extensions › Qrame**
or **Window › Extensions › Qrame Cont**.

### 4. The caption templates

The templates are now in Premiere's local templates folder, so they show up in
the **Essential Graphics** panel, and Qrame Cont finds them on its own when it
edits clips made from them.

For captions in Qrame, click the **MOGRT** button in the panel's bottom bar and
pick a template. The folder is hidden in the file dialog: press **⌘⇧G** and
paste `~/Library/Application Support/Adobe/Common/Motion Graphics Templates`.

The templates use the **Barlow** font family. If Premiere reports a missing
font, activate Barlow in Adobe Fonts (included with Creative Cloud) or install
it from Google Fonts. Both are free.

### 5. Extra setup for the automatic pipeline

Cutting from a finished SRT and everything in Qrame Cont work right after
installing. Silence Cut and the automatic pipeline need a few command-line
tools (ffmpeg and whisper-cpp from Homebrew, and a Whisper model) and, for the
model that picks the sections to keep, an API key. The **About** section of the
Qrame panel checks the machine, lists what is missing and gives the command for
each.

### Updating

Download the newer `.dmg` and run its `Install.command` the same way. It
replaces the installed panels and templates.

### If a panel does not appear

- If it is listed under **Window › Extensions** but nothing opens, it is usually
  open off-screen in the saved workspace. Choose **Window › Workspaces › Reset
  to Saved Layout**.
- If it is not listed at all, restart Premiere Pro once more. If it is still
  missing, run `Install.command` again and read what it reports.
