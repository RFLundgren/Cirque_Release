# Cirque Android Release

Cirque is a native Android music player for self-hosted Navidrome libraries. This repository is the public distribution point for the release APK, installation notes, user help, and release notes.

Cirque is closed-source and currently distributed directly for testing. It targets Android phone, tablet, Android Auto, and Android TV use, with one shared playback core and a growing set of device-specific interface refinements.

## Current Download

- APK: [downloads/cirque-0.1.161.apk](downloads/cirque-0.1.161.apk)
- Version: `0.1.161`
- Package: `com.cirque.music`
- Build type: signed release APK
- Minimum Android version: Android 8.0 / API 26

If Android warns that the app came from an unknown source, allow installation from your browser or file manager, then install the APK again.

## What Cirque Does

- Connects to your own Navidrome server with saved connection profiles for Local, VPN/Tailscale, domain/HTTPS, and fully custom setups
- Streams in original quality or MP3 transcode mode
- Supports background playback, lock-screen controls, Bluetooth media buttons, queue save/restore, and scrobbling
- Downloads albums and playlists for offline playback with storage limits, retry support, and Smart Sync
- Includes Android Auto support for safe in-car browsing and playback
- Includes Android TV support with a dedicated D-pad interface, TV Home, TV Library, TV Playing, QR-based phone-to-TV profile transfer, TV Pulse, and a dark listening screen
- Includes software DSP audio profiles with EQ, dynamics, route-based profile assignment, A/B bypass, meters, AutoEQ import, and room-measurement support
- Supports Pulse recaps where the server/plugin stack exposes them
- Supports Podcasts, Folders, AI Tags, and My Tags where the connected server exposes the required experimental endpoints

## Current Release Highlights

Version `0.1.161` includes the current Android TV parity work, Pulse story improvements, donationware prompt flow, and stronger Android Auto/playback persistence.

Recent areas of work include:

- Android TV Playing redesign with a dedicated footer mini-player dock, slimmer queue rows, better queue follow, dark listening mode, and stronger D-pad focus handling
- Android TV navigation parity work across Home, Library, detail screens, Settings, Search, and setup transfer
- Pulse Story pages that now carry more recap detail instead of leaving most information in Overview
- Donationware prompt flow on phone/tablet Home with cooldown logic and delayed permanent opt-out
- Android Auto queue/resume hardening for reconnect events, especially for podcasts and downloaded playlist sessions
- Restored queue recovery that refreshes remote stream URLs from the current connection to reduce stale source-not-found playback failures

## Device Compatibility

Cirque currently supports these device types:

- Android phones: primary day-to-day experience
- Android tablets: supported with shared app behaviour and ongoing layout polish
- Android Auto: supported for safe browsing and playback controls, including playlists and downloads
- Android TV: supported for living-room playback with TV-specific Home, Library, Playing, Pulse, Search, Settings, and setup-transfer flows

Android Auto and Android TV both use host-controlled or remote-driven layouts, so they do not always expose every phone/tablet interaction in the same way.

## Server Compatibility

Cirque works with standard Navidrome for the core Subsonic-style music client experience. Some newer areas are shown only when the connected server advertises the matching experimental endpoints or plugin data.

### Works With Standard Navidrome

- Connection profiles and server switching
- Albums, artists, songs, playlists, favorites, search, playback, queue, shuffle, repeat, and resume
- Background playback and Android system media controls
- Offline album and playlist downloads to the phone/tablet
- Android Auto core browsing/playback and downloaded collection playback
- Themes, accent colours, display settings, and audio profiles

### Requires Navidrome Experimental Or Companion Plugins

These areas are optional. Cirque probes the server and hides unsupported sections instead of exposing broken UI.

Important: not every experimental feature is available in every navidrome-experimental build. The `stable` tag is the safer checkpoint. The `develop` tag is where newer work appears first.

| Feature | Server channel | What Cirque uses it for |
| --- | --- | --- |
| Podcasts | `stable` and `develop` | Podcast browsing, episode playback, server-side podcast state, and podcast playlist workflows where supported |
| Physical folder browsing | `stable` and `develop` | Folders section for navigating and playing by disk layout |
| Enhanced scrobble attribution | Base attribution on `stable` and `develop`; newer breakdown cards require `develop` | Richer Pulse source/device/origin/playback-mode context |
| Pulse insights | Navidrome with plugin support plus the Pulse plugin | Weekly, monthly, and yearly recaps including listening, diversity, source, tag, podcast, and comparison insight cards where available |
| User-defined song tagging | `develop` only | My Tags and tag-based browsing/filtering |
| AI Genre / AI Mood / My Tags dashboards | `develop` only | Library dashboards and server-backed tag browsing |
| On-demand plugin actions | `develop` only | Manual plugin/server actions where supported |
| Skip / auto-pass disliked songs | `develop` only | Skipped-track indicators and automatic skip behaviour |
| Genre exploration and genre merging | `develop` only | Richer genre browsing and cleaner server genre data |

Experimental repositories:

- Navidrome experimental fork: [RFLundgren/navidrome_experimental](https://github.com/RFLundgren/navidrome_experimental)
- AI auto tagging plugin: [RFLundgren/AI-auto-tagging-plugin](https://github.com/RFLundgren/AI-auto-tagging-plugin)
- AI mood playlists plugin: [RFLundgren/AI-Mood-Playlists-Plugin](https://github.com/RFLundgren/AI-Mood-Playlists-Plugin)
- Pulse plugin and insight system: [RFLundgren/pulse](https://github.com/RFLundgren/pulse)

## Pulse Notes

Pulse is not part of the normal Subsonic API. It requires a Navidrome build with plugin support plus the Pulse plugin itself. Cirque reads the generated `Pulse-Data` snapshot payload and renders it as Overview and Story recap pages.

Pulse can provide weekly, monthly, and yearly recaps including top artists, tracks, albums, genres, moods, listening habits, sessions, streaks, diversity, recency, podcast insight fields, AI/My Tag patterns, comparison insights, source/device attribution, playback-origin attribution, streamed/downloaded breakdowns, and source/origin signatures where the server/plugin stack provides those fields.

Standard Navidrome ignores Cirque's additive attribution hints. Compatible navidrome-experimental and Pulse plugin builds are required before those extra source/origin cards appear.

## Installation

1. Download the current APK from this repository.
2. On your Android device, open Android settings and allow installs from your browser or file manager if prompted.
3. Open the APK and install it.
4. Open Cirque and complete the connection setup.

Updating is done by installing the newer APK over the existing app. Your saved connections, queue state, and downloads are preserved.

## First Test Checklist

1. Install the APK.
2. Open Cirque.
3. Add or import a connection profile.
4. Tap `Test Connection` before saving.
5. Confirm Library loads albums, artists, songs, and playlists.
6. Start playback and confirm Android notification controls appear.
7. If using downloads, download a small playlist or album and confirm it appears in Library > Downloads.
8. If using Android Auto, test normal playback, playlist playback, and reconnect resume.
9. If using Android TV, test Home, Library, Playing, Settings, and QR-based setup transfer.
10. If using the experimental server stack, confirm Podcasts, Folders, AI Tags, My Tags, skipped-track indicators, and Pulse appear only where your server supports them.

## Documentation

- Full user help: [HELP.md](HELP.md)
- Release notes: [RELEASE_NOTES.md](RELEASE_NOTES.md)
- Privacy note: [PRIVACY.md](PRIVACY.md)
- Third-party notices: [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
- Checksums: [SHA256SUMS.txt](SHA256SUMS.txt)

## Feedback

When reporting problems, include:

- Cirque version
- Android device model
- Android version
- Server version
- Connection type
- Whether you are using standard Navidrome or the experimental fork
- Whether the problem occurs on phone, tablet, Android Auto, or Android TV
