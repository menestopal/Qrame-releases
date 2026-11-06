# Qrame

Two panels for Premiere Pro. This repository holds no source code, only the
signed installer packages.

| Panel | What it does |
|---|---|
| **Qrame** | Re-cuts the active sequence by timecode and joins what is kept into a new, gap-free sequence. The original timeline is never touched. Three ways in: drop in a finished SRT; let Silence Cut measure the pauses and cut them out; or run the automatic pipeline, which transcribes the audio (locally with Whisper, or with Gladia) and lets a model pick the sections to keep from your prompt. It also places captions on the timeline. |
| **Qrame Cont** | Bulk MOGRT parameter editing, per-clip subtitle text editing, batch keyframe easing, and framing tools (QZoom, QPan, QStep). |

The two install, update and uninstall independently. You can install just one.

## Download

| Panel | Version | File |
|---|---|---|
| Qrame | — | not published yet |
| Qrame Cont | — | not published yet |

Older versions are on the [Releases](https://github.com/menestopal/Qrame-releases/releases) page.
Download only the `.zxp` file there. GitHub adds the "Source code" archives on
its own, and they are not needed for installing.

Requirements: Premiere Pro 25.0 or later. Tested on Premiere Pro 26.3 on macOS;
Windows has not been tested.

## Install

1. Quit Premiere Pro.
2. Install the `.zxp` with [ZXP Installer](https://aescripts.com/learn/zxp-installer/)
   (free, from aescripts) or Anastasiy's Extension Manager: drag the file onto
   its window. The packages are signed, so no developer setting has to be
   turned on.
3. Start Premiere Pro and open **Window › Extensions › Qrame** (or
   **Qrame Cont**).

To update, install the newer `.zxp` the same way. It replaces the old one.

### Setup for the automatic pipeline

Cutting from a finished SRT and everything in Qrame Cont work right after
installing. Silence Cut and the automatic pipeline need a few command-line
tools (ffmpeg and whisper-cpp from Homebrew, a Whisper model) and, for the
model that picks the sections, an API key. The **About** section of the Qrame
panel checks the machine, lists what is missing and gives the command for each.

### The panel does not appear

If it is listed under **Window › Extensions** but nothing opens, it is usually
open off-screen in the saved workspace: choose **Window › Workspaces › Reset
to Saved Layout**.
