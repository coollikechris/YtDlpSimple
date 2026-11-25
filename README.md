# YtDlpSimple

A lightweight Windows desktop interface for [yt-dlp](https://github.com/yt-dlp/yt-dlp). Paste a video link, choose a folder, and download using yt-dlp's default best-available format selection.

## Features

- Dark Windows Forms interface with download progress and cancellation.
- Remembers the selected save folder between runs.
- Pre-fills the URL field when the clipboard contains a YouTube or `youtu.be` link.
- Bundles yt-dlp and FFmpeg; no separate .NET runtime installation is needed.

## Use

Run `YtDlpSimple.exe` on Windows x64, paste a supported URL, choose a save folder, and click **Download**. On the first download, the bundled tools are extracted to `%LOCALAPPDATA%\YtDlpSimple\tools`. The save-folder preference is stored in `%APPDATA%\YtDlpSimple\settings.json`.

## Build

Building requires the .NET 8 SDK on Windows. From the repository directory, run:

```powershell
dotnet publish .\YtDlpSimple.csproj -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -p:IncludeNativeLibrariesForSelfExtract=true -o .\publish
```

The executable is written to `publish\YtDlpSimple.exe`. The project embeds the tools from `Assets\yt-dlp.exe` and `Assets\ffmpeg.exe`; keep those files in place when building.

## Third-party components

- **yt-dlp** — bundled in `Assets\yt-dlp.exe` (version `2026.11.23`). See its [license](https://github.com/yt-dlp/yt-dlp/blob/master/LICENSE).
- **FFmpeg** — bundled in `Assets\ffmpeg.exe` (build `N-124070-g75838b9c89`). The binary reports **GPL version 3 or later**; see [FFmpeg's legal information](https://ffmpeg.org/legal.html). This repository does not include the corresponding FFmpeg source or build configuration, which may be required when redistributing the bundled binary.

This repository does not currently include a license for YtDlpSimple's own source code. Add a repository license before granting others reuse rights.
