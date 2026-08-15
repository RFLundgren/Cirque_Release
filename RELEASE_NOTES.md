# Cirque Release Notes

## 0.1.161

This release refreshes the public APK in the `Cirque_Release` repository and brings the distribution docs back into line with the actual current app.

### Major Areas In This Build

- Android TV parity work across Home, Library, Search, Settings, setup transfer, and Playing
- Android TV Playing redesign with a dedicated footer mini-player dock, slimmer queue rows, stronger queue follow, and dark listening mode
- Pulse Story pages reworked to carry more of the recap detail instead of leaving most information in Overview
- Donationware prompt flow on phone/tablet Home with cooldown logic and delayed permanent opt-out
- Android Auto/playback persistence hardening for disconnect/reconnect scenarios, especially long podcast sessions and downloaded playlist sessions
- Queue restore now refreshes remote stream URLs from the active connection, reducing stale source-not-found playback failures after returning to an older queue

### Platform Notes

- Android Auto remains host-controlled, so some compact layouts may still omit artwork even when Cirque provides it
- Android TV is actively supported, but ongoing polish still focuses on real-device focus/navigation tuning and visual density
- Standard Navidrome continues to support the core app; Podcasts, Folders, AI Tags, My Tags, skipped-track indicators, and some Pulse insight cards still depend on the matching experimental server/plugin stack

## 0.1.132

- Playback queue snapshots now persist on more playback-state transitions, which improves resume after Android Auto/Bluetooth disconnects.
- Restored playback queues now rebuild remote stream URLs from the current active connection instead of replaying stale saved URLs.

## 0.1.131

- Donation reminder flow introduced on phone/tablet Home after meaningful use.
- Not now now applies a cooldown and permanent opt-out is intentionally delayed until later reminder appearances.

## 0.1.129

- Pulse Story pages now carry substantially more recap detail.
- Story chapters for tracks, albums, genres, sources, and closing cards are denser and more informative.

## 0.1.128

- Android TV Playing moved to a clearer two-region layout.
- TV footer mini-player dock added.
- Queue rows were slimmed back down and queue focus handoff was hardened.

## 0.1.114

- Android TV focus ownership, connection transfer, accent-following highlight, and exit behaviour were significantly improved.

## 0.1.101

- Earlier public release repository refresh with Android Auto queue persistence, Android TV dark listening screen, and Pulse/source-attribution support improvements.
