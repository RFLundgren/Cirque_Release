# Cirque Help

This help file is written for new users. It explains what Cirque does, how to connect it to a server, which features work with standard Navidrome, and which features require the experimental server or companion plugins.

## What Cirque Is

Cirque is an Android music client for Navidrome and compatible Subsonic API servers. It is designed around private self-hosted music libraries, offline use, phones, tablets, Android Auto, Android TV listening, and richer library discovery.

Cirque does not include a music server. You must already have a reachable Navidrome or Subsonic-style server.

## Device Compatibility

Cirque currently supports Android phones, Android tablets, Android Auto, and Android TV.

Phones are the primary experience. Tablets use the same core app features, with larger-screen layout polish still evolving. Android Auto is intended for simple in-car playback and safe browsing. Android TV is intended for playback-focused listening, including a dark listening screen for people who want music without a bright TV image.

Android Auto and Android TV do not work exactly like the phone app. They use platform-controlled layouts, so some app themes, colors, advanced controls, and detailed screens may not appear the same way.

## Install And Confirm The Build

1. Download `downloads/cirque-0.1.101.apk` from this repository.
2. Install the APK on your Android device.
3. Open Cirque.
4. Open Settings.
5. Open About.
6. Confirm the package is `com.cirque.music`.
7. Confirm the version is `0.1.101`.

If you previously installed an early prototype using a different package name, uninstall the old app to avoid confusion.

## Standard Navidrome Versus Experimental Features

Cirque works safely against standard Navidrome. Experimental features are capability-gated: if the server does not support a feature, Cirque should hide that screen or action.

Standard Navidrome supports the core music experience: browsing albums, artists, songs, playlists and favorites; search; playback; artwork; queue controls; playlist editing where supported; offline downloads; scrobbling; themes; audio profiles; and Android media controls.

Navidrome experimental and companion plugins unlock optional features such as Podcasts, Folders, AI Tags, My Tags, skipped track metadata, AI playlist workflows, and Pulse insights.

Related repositories:

- Navidrome experimental fork: https://github.com/RFLundgren/navidrome_experimental
- AI auto tagging plugin: https://github.com/RFLundgren/AI-auto-tagging-plugin
- AI mood playlists plugin: https://github.com/RFLundgren/AI-Mood-Playlists-Plugin
- Pulse: https://github.com/RFLundgren/pulse

## Before You Connect

You need:

- An Android phone, tablet, Android TV device, or Android Auto-capable phone.
- A running Navidrome or compatible Subsonic API server.
- The server address and port.
- Your server username and password.
- Network access from the Android device to the server.

Common server examples:

```text
Local:      http://192.168.1.50:4533
Tailscale:  http://100.x.y.z:4533
Domain:     https://music.example.com
```

When away from home on mobile data, the phone still needs a path back to the home server. Usually this means Tailscale, WireGuard, another VPN, or a public HTTPS reverse proxy.

## First Run Setup

1. Open Cirque.
2. Choose a connection type.
3. Enter the server address.
4. Confirm the port, normally `4533` for Navidrome.
5. Choose HTTP or HTTPS.
6. Enter username and password.
7. Choose Original or Transcode MP3 streaming.
8. Tap `Test Connection`.
9. Save only after the test succeeds.

Connection types:

- Local: use when the phone and server are on the same home network.
- Tailscale/VPN: use when the phone reaches the server through a private remote network.
- Domain/HTTPS: use when the server is exposed through a secure domain or reverse proxy.
- Custom: use when you want to enter exact details manually.

## Connection Profiles

Cirque supports named connection profiles, similar to the Windows desktop app. This allows you to keep separate profiles for production, test, local network, VPN, or a public domain.

1. Open Settings.
2. Open Connection.
3. Create or select a saved profile.
4. Enter the profile name and server details.
5. Test and save.
6. Switch profiles later by selecting another saved profile.

Cirque can also use automatic profile selection for home network, away/VPN network, and mobile fallback routes. Mobile access still needs a reachable route to your server, normally through VPN/Tailscale or HTTPS.

## Home

Home is the quick-start screen. It shows useful entry points and recently available library content.

Typical actions:

- Open Library.
- Open Offline Downloads.
- Open Search.
- Open Smart Mix Builder.
- Continue recent listening.
- Open recently added or random albums.

Home shortcut chips can be adjusted in Settings > Display.

## Library

Library is the main browsing area.

Available standard sections:

- Albums
- Artists
- Songs
- Playlists
- Favorites
- Downloads
- Genres

Experimental sections appear only when supported by the server:

- Podcasts
- Folders
- AI Tags
- My Tags

Each section supports list/grid behavior where appropriate. Selected chips should use the current theme and accent color.

## Albums, Artists, Songs, And Favorites

Albums lets you browse and play albums. Artists opens artist detail pages. Songs provides a direct track list. Favorites reflects starred artists, albums, and songs from the server.

You can start playback from rows, open details, add songs or albums to playlists, and download supported albums or playlists to the phone.

Skipped/disliked tracks appear dimmed when the connected server exposes skip metadata. This is an experimental-server feature.

## Playlists

Playlists come from the server. You can open a playlist, play it in order, play selected tracks, edit playlist contents where supported, and download playlists to the phone.

Downloaded playlists are especially useful for Android Auto because playback can start without waiting for the server or mobile network.

## Downloads

Downloads are stored in Cirque's app-private storage on the Android device. Removing Cirque may remove these files.

To download music:

1. Open an album or playlist.
2. Use the three-dot menu.
3. Choose the download action.
4. Wait for the progress and completion message.
5. Open Library > Downloads to play it offline.

Download settings include Wi-Fi-only protection and storage limit controls.

## Podcasts

Podcasts appear only when the connected server supports the podcast extension.

Podcast actions include:

- Browse podcast channels.
- Open channel episodes.
- Play an episode.
- Request server-side episode download where supported.
- Download an episode to the phone.
- Add downloaded server episodes to playlists where the server exposes them as playable items.

Server-side download and phone download are separate. A server-side download caches the episode on the server. A phone download saves it locally for Cirque offline playback.

## Folders

Folders appear only when the server supports physical folder browsing.

You can browse folder roots, open subfolders, and play visible tracks. Full recursive folder actions are not currently built.

## AI Tags And My Tags

AI Tags and My Tags require the experimental Navidrome tag endpoints.

AI Tags are generated or managed by the experimental AI tagging path. Cirque can show category entry points for Genre, Language, and Mood, depending on what is enabled in Settings > Display.

My Tags are user-owned tags exposed by the experimental server. They are separate from AI Tags. If no user tags exist, My Tags may be hidden or empty.

Genre, AI Tags, and My Tags use gradient tiles with the visible genre, mood, language, or tag name inside the tile.

## Smart Mix Builder

Smart Mix Builder creates playback mixes from available library metadata. Current mix options include criteria such as genre and decade where server data allows it.

Genre plus decade filtering is intended to act as a combined filter: for example, rock from the 1980s, not rock plus all 1980s tracks.

## Search

Search finds artists, albums, and songs. Recent searches are saved locally on the device. Starting playback from a search result creates a queue from the visible track results.

## Now Playing

Now Playing includes artwork, track details, transport controls, seek position, shuffle, repeat, Up Next queue, queue editing, and Save Queue as Playlist.

Shuffle is a toggle. Repeat cycles through off, all, and one.

## Android Auto

Cirque supports Android Auto for core playback and library actions. It is intended to be simple and safe in the car.

Current Android Auto behavior includes:

- Browse supported media roots.
- Play albums, playlists, and downloads.
- Use playback controls from the car screen.
- Use downloaded playlists for more reliable in-car switching.
- Cirque supplies artwork through Android media metadata, but Android Auto controls final layout. Some compact split-screen layouts may hide artwork even when Cirque provides it.

## Android TV

Cirque includes early Android TV support focused on playback. On TV, the Now Playing screen can offer a dark listening mode so music can continue while the screen is blacked out. This is useful when listening at night or falling asleep.

Cirque cannot reliably turn every TV panel off from inside the app. The dark screen mode is the safer app-level option.

## Themes And Display

Settings > Display includes theme selection, accent color selection, custom color support, Home shortcut visibility, Downloads chip visibility, AI Tags category visibility, and control strip position.

The selected app theme affects the Android app UI. Android Auto has strict host-controlled UI limits, so it may not fully mirror the in-app theme.

## Audio Profiles And Sound Tuning

Cirque includes audio profile settings for users who want more control over playback sound. The current implementation is an early staged version, with support for named profiles and visible EQ bands with frequency labels.

The long-term direction is a more advanced sound-tuning system with parametric EQ, compression, loudness options, and profile assignment for headphones, earbuds, car audio, and other listening devices.

## Pulse

Pulse is an optional insight system. It is separate from standard Navidrome and requires the Pulse plugin/data path.

Pulse can surface listening behavior insights such as library variety, repeated listening, top artist share, time patterns, source/device context where reported by Cirque, and other deeper summaries as the plugin and app evolve.

If you run standard Navidrome or an older Pulse plugin, unsupported Pulse cards should stay hidden.

## Diagnostics And Support

Cirque includes diagnostics intended to help troubleshoot crashes, Android Auto issues, downloads, playback, and connection problems without filling logs with normal playback noise.

Support bundle creation is designed to collect useful non-sensitive context such as app/device version, settings state, diagnostics, and playback/download state. Where possible it opens the user's default email app addressed to Cirque support.

## Privacy

Cirque does not include analytics, advertising, or tracking SDKs. It stores connection details, preferences, recent searches, queue state, and chosen offline downloads locally on the device.

Cirque does not store your raw server password after a successful save. It stores Subsonic token/salt credentials for server authentication.

## Troubleshooting

If Cirque cannot connect:

1. Open the server URL in the phone browser.
2. Confirm HTTP versus HTTPS.
3. Confirm the port.
4. Confirm username and password.
5. Confirm VPN/Tailscale is connected if away from home.
6. Use Test Connection in Settings.

If a feature is missing:

1. Confirm whether it requires experimental server support.
2. Confirm you are connected to the intended server profile.
3. Pull down to refresh the Library screen.
4. Restart Cirque after switching server builds.

If playback starts from the wrong place:

1. Stop playback.
2. Start the intended album, playlist, podcast, or download again.
3. Confirm the queue on Now Playing.
4. For car use, prefer downloaded playlists where possible.

If Bluetooth is connected but silent:

1. Confirm Android media volume.
2. Confirm the Bluetooth device is selected as the active output.
3. Try another app to confirm the audio route.
4. Toggle Bluetooth off and on.
5. Restart playback in Cirque.

If downloads are blocked:

1. Check Settings > Offline & Downloads.
2. Confirm Wi-Fi-only download protection is not blocking mobile data.
3. Confirm there is enough app storage available.
4. Remove old downloads or raise the storage limit.

## Reporting Issues

When reporting a problem, include Cirque version, Android device model, Android version, whether Android Auto or Android TV was involved, server type, plugin versions if using experimental features, connection type, what you tapped immediately before the problem, and whether the issue repeats every time or only sometimes.
