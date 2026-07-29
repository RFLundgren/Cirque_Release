# Cirque Help

Cirque is an Android music client for Navidrome and compatible Subsonic API servers. This guide is written as a practical user manual: find the thing you want to do, follow the steps, then use the checks at the end of the section if something does not work.

The current build is focused on Android phones. Tablet and Android TV work is still evolving, but this help file mainly describes the phone experience that is available now. Android Auto support already exists for core playback and queue actions.

## Index

1. [Confirm You Are On The Right Build](#confirm-you-are-on-the-right-build)
2. [Before You Connect](#before-you-connect)
3. [First Run Setup](#first-run-setup)
4. [Connection Types](#connection-types)
5. [Settings And Saved Connections](#settings-and-saved-connections)
6. [Offline Mode](#offline-mode)
7. [Home](#home)
8. [Library Albums](#library-albums)
9. [Library Artists](#library-artists)
10. [Library Songs](#library-songs)
11. [Library Playlists](#library-playlists)
12. [Library Favorites](#library-favorites)
13. [Library Downloads](#library-downloads)
14. [Skip / Dislike Songs](#skip--dislike-songs)
15. [Library AI Tags](#library-ai-tags)
16. [Library Podcasts](#library-podcasts)
17. [Library Folders](#library-folders)
18. [Search](#search)
19. [Album Detail And Starting Playback](#album-detail-and-starting-playback)
20. [Mini-Player](#mini-player)
21. [Playing Screen](#playing-screen)
22. [Queue, Shuffle, And Repeat](#queue-shuffle-and-repeat)
23. [Download Network And Storage Settings](#download-network-and-storage-settings)
24. [Streaming Quality](#streaming-quality)
25. [Background Playback And System Controls](#background-playback-and-system-controls)
26. [Bluetooth Audio](#bluetooth-audio)
27. [Pulse](#pulse)
28. [Donationware](#donationware)
29. [Troubleshooting](#troubleshooting)
30. [What Is Still Planned](#what-is-still-planned)
31. [Project Tracking](#project-tracking)

## Confirm You Are On The Right Build

Use this section after installing a new APK, especially if a feature appears to be missing.

### How to check

1. Open Cirque.
2. Open `Settings`.
3. Find `About`.
4. Confirm the app name is `Cirque`.
5. Confirm the package is `com.cirque.music`.
6. Confirm the version shown in About matches the newest APK you installed.

### Current debug APK

```text
C:\Development\Navidrome Streamer\app\build\outputs\apk\debug\app-debug.apk
```

### Note

- The old prototype used a different package. If Android still shows the old app, uninstall `com.navidromestreamer`.
- The current build is primarily phone-focused, with Android Auto and Android TV support also available for playback-focused testing.

## Before You Connect

Cirque needs a reachable Navidrome or Subsonic-compatible server before it can show your music.

### You need

- An Android phone.
- A running Navidrome server or compatible Subsonic API server.
- The server address, such as an IP address, hostname, MagicDNS name, or domain.
- The server port. Standard Navidrome is usually `4533`.
- The protocol: `HTTP` or `HTTPS`.
- Your Navidrome username.
- Your Navidrome password.
- Network access from the phone to the server.

### Common examples

Local Navidrome server:

```text
Address: 192.168.1.50
Port: 4533
Protocol: HTTP
```

Tailscale server:

```text
Address: 100.100.100.50
Port: 4533
Protocol: HTTP
```

HTTPS reverse proxy:

```text
Address: music.example.com
Port: 443
Protocol: HTTPS
```

You can paste a full URL into the Address field. Cirque will split it into address, port, and HTTP/HTTPS.

Examples:

```text
http://192.168.1.50:4533
https://music.example.com
https://music.example.com:8443
```

## First Run Setup

First Run Setup appears automatically when no server is saved.

### How to use it

1. Open Cirque.
2. Read the phone-focused build notice.
3. Choose the connection type before entering the address.
4. Use `Local` if the phone and server are on the same Wi-Fi.
5. Use `Tailscale/VPN` if the phone reaches the server through Tailscale, MagicDNS, WireGuard, or another VPN.
6. Use `Domain/HTTPS` if you use a reverse proxy or public domain.
7. Use `Custom` if you know the exact address, port, and protocol.
8. Enter the server Address.
9. Check Port. The default is `4533`.
10. Select `HTTP` or `HTTPS`. The active chip is highlighted.
11. Enter your username.
12. Enter your password.
13. Choose `Original` or `Transcode MP3` streaming.
14. Tap `Test Connection`.
15. Read the success or error dialog.
16. Tap `Test and Save` when the connection works.

### Auto-detect during setup

Use `Auto-detect Server` only when all of these are true:

- Connection type is `Local`.
- Your phone is on the same Wi-Fi as the server.
- Navidrome is reachable on the port shown in the Port field.
- The selected `HTTP` or `HTTPS` option matches the local server.

Auto-detect scans the current local subnet using the selected port and protocol. It does not search Tailscale, VPN, public domains, reverse proxy names, or custom internet routes.

### If setup fails

- Confirm the server opens in the phone browser.
- Confirm Tailscale or the VPN is connected before testing a VPN address.
- Confirm the port is correct.
- Confirm the HTTP/HTTPS selection matches the address you use in a browser.
- Re-enter the password carefully and test again.

## Connection Types

Connection type controls how Cirque tests and saves your server details.

### Local

Use `Local` for a server on the same Wi-Fi network.

Steps:

1. Select `Local`.
2. Tap `Auto-detect Server`, or type the local IP address manually.
3. Leave Port as `4533` unless your Navidrome server uses a different port.
4. Select `HTTP` for a normal local Navidrome server, or `HTTPS` if your local server is configured for TLS.
5. Enter username and password.
6. Tap `Test Connection`.
7. Save when successful.

### Tailscale/VPN

Use `Tailscale/VPN` when the phone reaches Navidrome through a private network.

Steps:

1. Connect Tailscale or your VPN on the phone.
2. Select `Tailscale/VPN`.
3. Enter the Tailscale IP, MagicDNS name, VPN hostname, or VPN IP.
4. Leave Port as `4533` unless your server uses another port.
5. Select `HTTP` unless you configured TLS for that private address.
6. Enter username and password.
7. Tap `Test Connection`.
8. Save when successful.

Examples:

```text
music-server
music-server.tailnet-name.ts.net
100.100.100.50
```

### Domain/HTTPS

Use `Domain/HTTPS` for a public domain or reverse proxy.

Steps:

1. Select `Domain/HTTPS`.
2. Enter the domain, for example `music.example.com`.
3. Select `HTTPS`.
4. Use Port `443` for normal HTTPS, or the custom port your proxy uses.
5. Enter username and password.
6. Tap `Test Connection`.
7. Save when successful.

### Custom

Use `Custom` when you want Cirque to test exactly what you enter.

Steps:

1. Select `Custom`.
2. Enter the exact address.
3. Enter the exact port.
4. Select the exact protocol.
5. Enter username and password.
6. Tap `Test Connection`.
7. Save when successful.

### Saved profiles

Cirque now supports desktop-style named saved profiles. Each saved profile stores its own connection type, address, port, HTTP/HTTPS choice, username, and secure login token.

How to use profiles:

1. Open `Settings`.
2. Tap `Connection`.
3. Under `Saved Profiles`, tap an existing profile to make it active, or tap `New Profile` to create another one.
4. Enter a profile name such as `Production`, `Test`, `Travel VPN`, or `Local Backup`.
5. Choose the connection type that fits that profile: `Local`, `Tailscale/VPN`, `Domain/HTTPS`, or `Custom`.
6. Enter the server details.
7. Tap `Test and Save`.
8. Return later and tap any saved profile to switch to it.

For Domain/HTTPS, paste the browser URL into Address when you are unsure. Cirque uses that manual hint to fill the domain, port, and HTTPS choice.

## Settings And Saved Connections

Settings opens as a menu of focused pages instead of one long form. Use it to update connection details, change streaming mode, turn Offline Mode on or off, control downloads, change display chips, review planned features, read About, and access donation links.

Connection also includes automatic profile selection. You can choose which saved profile Cirque should use for home network, away network / Tailscale, and mobile fallback.

### Settings pages

- `Connection`: server profiles, address, port, username, password, test, save, and clear.
- `Playback`: streaming mode and future playback options.
- `Offline & Downloads`: Offline Mode, download network protection, storage limit, and download location.
- `Display`: Home shortcut chips, Downloads filter chips, AI Tags category visibility, theme, accent, and control-strip position.
- `Future Features`: disabled placeholders for features that may be built later.
- `About & Support`: version, package, current device support, and donationware links.

### Update the saved connection

1. Open `Settings`.
2. Tap `Connection`.
3. Select the saved profile you want to edit.
4. Change the profile name, connection type, Address, Port, HTTP/HTTPS, Username, or Password as needed.
5. Enter the password if you changed any connection detail and Cirque cannot reuse the saved credentials.
6. Tap `Test Connection`.
7. Tap `Update and Save` when the test works.

### Clear the current profile

1. Open `Settings`.
2. Tap `Connection`.
3. Select the saved profile you want to remove.
4. Tap `Clear Current Profile`.
5. Cirque removes that saved profile.
6. If another profile exists, Cirque makes another saved profile active. If no profiles remain, the app returns to setup.

### Password behavior

Cirque does not store the raw password. When you save, Cirque stores token/salt credentials for the Subsonic API.

This means:

- The password field is blank after saving.
- A blank password field after saving is expected.
- You do not need to re-enter the password every time you open Cirque.
- You do need to re-enter the password when changing or recreating the connection.

### Offline Mode

1. Open `Settings`.
2. Tap `Offline & Downloads`.
3. Find `Offline Mode`.
4. Tap `Offline Downloads` to use downloaded albums and playlists only.
5. Tap `Online Library` to return to normal server browsing and streaming.

When Offline Mode is on, Home does not try to load server shelves and Library opens directly to downloaded music. This is useful when travelling, using airplane mode, or when your server is temporarily unreachable.

### Display options

1. Open `Settings`.
2. Tap `Display`.
3. Under `Home chips`, select the shortcut chips you want to see on Home.
4. Under `Downloads chips`, select the filters you want to see in `Library` > `Downloads`.
5. Under `AI Tag categories`, choose whether `Genre`, `Language`, and `Mood` appear inside the AI Tags submenu.
6. Leave only the chips you use. For example, keep only `Playlists` under Downloads if you only want downloaded playlists visible there.

At least one chip stays enabled in each group so Home, Downloads, and AI Tags remain usable.

### Download protection

1. Open `Settings`.
2. Tap `Offline & Downloads`.
3. Find `Downloads`.
4. Choose `Wi-Fi only` if you do not want album or playlist downloads to use phone data.
5. Choose `Wi-Fi + phone data` only if you are comfortable using mobile data for downloads.
6. Review the recommended storage limit.
7. Change `Download storage limit in MB` if you want Cirque to allow more or less download storage.
8. Tap `Use recommended` if you want Cirque to return to its calculated default.

Cirque calculates the default from storage currently available to the app. The default is deliberately conservative so downloads do not unexpectedly fill the phone.

## Home

Home is the quick browsing screen. It loads shelves that are useful for starting playback quickly.

### How to use it

1. Open `Home`.
2. Wait for the loading indicator to finish.
3. Confirm the status reads `Connected: <profile>`, for example `Connected: Tailscale/VPN`.
4. Swipe down from the top of Home whenever you want to reload the Home shelves without leaving Home.
5. Browse `Recently Added`.
6. Browse `Random Albums`.
7. Browse `A-Z Albums`.
8. Tap an album tile to open Album Detail.
9. Use the `Library` chip for structured browsing.
10. Use the `Offline Downloads` chip to go straight to albums and playlists available for offline playback.
11. Use the `Search` chip to find a specific artist, album, or track.

### Note

- Artwork appears when Navidrome provides cover art.
- If artwork is missing, Cirque shows a letter placeholder.
- Home does not show the raw server URL during normal connected state.
- The Home shortcut chips wrap onto extra lines when the phone screen is too narrow.
- When Offline Mode is on, Home shows an offline message instead of contacting the server.

## Library Albums

Library Albums gives you a larger album browsing view than Home.

### How to use it

1. Open `Library`.
2. Tap `Albums`.
3. Swipe down from the top of Library whenever you want to reload the current Library section.
4. Choose a sort: `A-Z`, `Recently Added`, or `Random`.
5. Choose `List` or `Grid`.
6. Tap an album.
7. On Album Detail, tap `Play Album` or choose a track.

### Sort choices

- `A-Z` sorts by album name.
- `Recently Added` shows newer albums first.
- `Random` asks Navidrome for a random selection.

### Layout choices

- `List` shows compact rows.
- `Grid` shows larger album tiles.
- Albums remembers its own List/Grid setting after restarting the app.
- Library chips wrap onto extra lines when needed, and the selected chip is highlighted instead of adding `Active` text.

## Library Artists

Library Artists lets you browse artists and open Artist Detail.

### How to use it

1. Open `Library`.
2. Tap `Artists`.
3. Choose `List` or `Grid`.
4. Tap an artist.
5. Review albums by that artist.
6. Tap an album to open Album Detail.

### Note

- Artists remembers its own List/Grid setting separately from Albums.
- Artist Detail currently focuses on albums.
- Artist top tracks are not built yet.

## Library Songs

Library Songs loads playable tracks from Navidrome so you can start listening without first choosing an album.

### How to use it

1. Open `Library`.
2. Tap `Songs`.
3. Choose `List` or `Grid`.
4. Tap a song to start playback from the Songs queue.
5. Use the mini-player for quick control.
6. Open `Playing` for seek, shuffle, repeat, and queue controls.

### Note

- Songs uses a live server-provided song list.
- Song title, artist, album, artwork, and duration appear when Navidrome provides them.
- Songs remembers its own List/Grid setting separately from Albums, Artists, Playlists, and Favorites.
- Next and previous follow the Songs queue after playback starts from this section.
- Use the vertical three-dot song menu to add a song to a new or existing playlist.

### If songs do not appear

1. Confirm Navidrome has tracks.
2. Open `Settings`.
3. Tap `Test Connection`.
4. Retry Songs.
5. If a row has limited metadata, check what Navidrome shows for that track.

## Library Playlists

Library Playlists loads your Navidrome playlists and opens a playlist detail screen with playable tracks.

### How to use it

1. Open `Library`.
2. Tap `Playlists`.
3. Choose `List` or `Grid`.
4. Tap a playlist.
5. Tap `Play Playlist` to start from the first track, or tap a specific track.
6. Open `Playing` to view and edit the queue created from that playlist.

### Playlist Detail

- Playlist Detail shows the playlist track list.
- The current playlist track is highlighted while it is playing.
- The mini-player remains visible at the bottom of Playlist Detail.
- Track durations appear when Navidrome provides them.
- Playlists remembers its own List/Grid setting.
- Use the vertical three-dot menu on a playlist track to add it to another playlist or remove it from the current playlist.

### If playlists do not appear

1. Confirm playlists exist in Navidrome for the same user account.
2. Open `Settings`.
3. Tap `Test Connection`.
4. Retry Playlists.
5. If a playlist opens empty, check the playlist contents in Navidrome.

## Library Favorites

Library Favorites loads starred artists, albums, and songs from Navidrome.

### How to use it

1. Open `Library`.
2. Tap `Favorites`.
3. Choose `List` or `Grid`.
4. Tap a favorite artist to open Artist Detail.
5. Tap a favorite album to open Album Detail.
6. Tap a favorite song to start playback from the favorite songs queue.

### Note

- Favorites reflects what is starred in Navidrome.
- Favorites may contain a mix of artists, albums, and songs.
- Favorites remembers its own List/Grid setting.
- Next and previous follow the favorite songs queue after playback starts from a favorite song.
- Favorite song rows include the vertical three-dot song menu for adding that song to a playlist.

### If favorites do not appear

1. Star an artist, album, or song in Navidrome.
2. Return to Cirque.
3. Open `Library`.
4. Tap `Favorites`.
5. Tap `Retry` if the screen is still empty.

## Library Downloads

Library Downloads lists albums and playlists you have saved to this phone. It is the first-pass offline library for Cirque.

### How to download music

1. Connect to your Navidrome server.
2. Download an album from an album three-dot menu, or download a playlist from a playlist three-dot menu.
3. Keep Cirque open until the progress message says the download completed.
4. Read the completion message if you want the exact destination folder.

### How to play offline

1. Open `Library`.
2. Tap `Downloads`.
3. Choose `All`, `Albums`, `Artists`, `Songs`, or `Playlists`.
4. Read the status line. It shows the app-private storage location when downloaded items are present.
5. Tap a downloaded album or playlist.
6. Cirque builds a queue from the local files and starts playback.
7. To confirm offline playback, disconnect from the server network or enable airplane mode after the download has completed, then play from `Library` > `Downloads`.

From Home, tap `Offline Downloads` to open this same page directly.

You can also turn on `Settings` > `Offline Mode` > `Offline Downloads`. With Offline Mode on, tapping the main `Library` tab opens Downloads directly.

### How to remove downloads

1. Open `Library`.
2. Tap `Downloads`.
3. Find the downloaded album or playlist.
4. Tap `Remove`.
5. Cirque deletes the local files for that downloaded item.

### Note

- Downloads are stored under Cirque's app-private Music downloads folder, normally `Android/data/com.cirque.music/files/Music/Cirque Downloads`.
- Android removes app-private downloads if Cirque is uninstalled.
- Removing a download does not delete the album, playlist, or track from Navidrome.
- Downloaded playback uses local file URLs, so the server is not needed after the download is complete.
- Downloads is offline-only. Its filters never load the live Navidrome library.
- Albums and Playlists show downloaded collections.
- Artists is built from the artist metadata on downloaded tracks.
- Songs shows the downloaded tracks themselves.
- If a downloaded track has no artist metadata, it may not appear under Artists.
- Tap `Show full Library` when you want to leave Downloads and return to the live Library sections. This button is hidden while Offline Mode is on; turn Offline Mode off in Settings first.
- Swipe down from the top of Downloads to rescan the local download list.

### If downloads do not appear or play

1. Confirm the original download finished successfully.
2. Return to `Library`.
3. Tap `Downloads`.
4. Tap `Retry` if the list is empty.
5. If a downloaded item still does not play offline, remove it and download it again while connected to the server.

## Skip / Dislike Songs

Skip / Dislike Songs is a server-specific feature supported by navidrome-experimental and Cirque. Standard Navidrome does not expose this feature, so Cirque hides Skip / Unskip actions unless the connected server confirms support. When available, it lets you mark individual songs so Cirque avoids auto-playing them while still allowing you to play them deliberately when you choose.

### How to use it

1. Open a song's three-dot menu from `Library`, `Search`, `Album Detail`, `Artist Detail`, `Playlist Detail`, or another song list.
2. Tap `Skip song` to flag that song on the server for your account.
3. The song row is greyed out and shows a small `Skipped` chip so it is obvious that the song is currently skipped.
4. Tap the song directly if you still want to hear it on purpose.
5. Open the same menu later and tap `Unskip song` to restore normal auto-play behaviour.

### What Cirque does with skipped songs

- Cirque filters skipped songs out when it builds a fresh queue.
- If you explicitly tap a skipped song to start playback, Cirque still lets that one track play.
- Cirque re-checks skip state again when playback advances, so a song you skip after it was already queued can still be bypassed before it starts.
- Skip is per-user, not global. Another user can keep a different skip list on the same server.

### Important note

This is not a standard Subsonic or OpenSubsonic feature. It only works against server builds that implement the navidrome-experimental `skip` and `unskip` endpoints. Generic Subsonic clients will usually ignore it.

### If it does not work

1. If Skip song is missing from the song menu, the connected server has not confirmed support for this fork-specific feature. Standard Navidrome hides this action.
2. If another client ignores skipped songs, that client probably has not implemented this fork-specific feature yet.
3. If you want to hear a skipped song anyway, tap it directly. Skip blocks auto-play, not deliberate manual play.

## Library AI Tags And My Tags

Library AI Tags and My Tags appear only when the connected server supports the relevant Cirque-compatible tag endpoints. Standard Navidrome does not expose these endpoints, so Cirque hides these sections completely on standard servers.

### How to use it

1. Open `Library`.
2. Tap `AI Tags` or `My Tags` if either section is visible.
3. Use `Filter current section` to narrow the visible tag list.
4. Tap a tag to see songs carrying that exact tag.
5. Tap a song to play from the visible tagged-song list.
6. Tap `Back to Tags` to return to the tag list.
7. Pull down to refresh the current tag view.

### Notes

- AI Tags are read from the fork-specific Subsonic AI tag endpoints used by the AI auto-tagging workflow. Cirque splits AI Tags into Genre, Language, and Mood by the server tag prefixes `genre:`, `language:`, and `mood:`.
- My Tags are read from the fork-specific Subsonic My Tags endpoints and show tags manually added by the current user in navidrome-experimental.
- Cirque probes the server before showing each tag section. If the matching endpoint is missing or returns an error, that section is hidden.
- The current Android view lists tag names and lets you browse the songs behind each tag. Prefixes are hidden in the UI, so `mood:Chill` appears as `Chill` under Mood. Tag entries use the same deterministic gradient artwork style as Library Genres, with the tag name shown inside the gradient tile so the list is easier to scan visually. It does not yet show per-tag counts because the current Subsonic tag endpoints return names, not counts.
- AI Tags and My Tags are separate on the server. A tag can exist in one section without appearing in the other.

### If AI Tags or My Tags is missing

1. Confirm you are connected to a server build that includes the AI tag Subsonic endpoints.
2. Confirm the current user has AI tags on the server.
3. Pull down to refresh Library after switching connection profiles or server builds.
4. If you are using standard Navidrome, this is expected: AI Tags and My Tags remain hidden.
## Library Podcasts

Library Podcasts appears only when the connected server supports the Subsonic podcast extension. If the server does not support it, Cirque hides the Podcasts section completely.

### How to use it

1. Open `Library`.
2. Tap `Podcasts` if it is visible.
3. Tap a podcast channel to open its episodes.
4. Tap an episode to start playback.
5. Use the episode three-dot menu when you want more actions.
6. Pull down to refresh the channel or podcast list.

### Episode actions

- `Download to phone` saves the episode into Cirque's normal app-private offline storage on this device.
- `Download episode on server` sends the server's podcast-download request. This is a server-side cache/download action, not the phone download itself.
- `Add to playlist` appears when the server reports that the episode is already downloaded and usable as a normal playable item.

### Episode status lines

- `Server: Not downloaded yet` means the server knows about the episode but has not downloaded or cached it yet.
- `Server: Downloading` means the server reports that its own podcast download is in progress.
- `Server: Downloaded` means the server reports the episode as downloaded and ready.
- `Server: Stream only / not downloaded` means the server is exposing it as streamable content without a completed downloaded cache entry.
- `Downloading to phone` and `Downloaded to phone` refer to Cirque's local offline copy on your device, separate from the server state.

### Notes

- Cirque briefly auto-refreshes the current podcast channel after you request a server-side download so the row status can update without leaving and re-entering the screen.
- Some custom Navidrome podcast builds return incomplete bulk podcast payloads. Cirque uses fallback loading so an individual channel may still work even if the full podcast response is incomplete.
- Podcast playback uses the same normal playback path as music playback. There is no separate podcast player.

### If Podcasts is missing or not updating

1. Confirm the connected server actually supports the podcast extension.
2. Pull down to refresh the Podcasts view.
3. If you requested `Download episode on server`, give the server a moment to update its own state and then refresh again.
4. If episode rows look incomplete, confirm the channel and episode metadata are visible on the server side.

## Library Folders

Library Folders appears only when the connected server supports physical folder browsing. If the server does not support it, Cirque hides the Folders section completely.

### How to use it

1. Open `Library`.
2. Tap `Folders` if it is visible.
3. Tap a folder root to open it.
4. Tap a subfolder to go deeper.
5. Tap a track to start playback from the visible folder level.
6. Pull down to refresh the current folder view.

### Notes

- The current Android implementation is intentionally one level at a time.
- Folder rows can contain both subfolders and tracks.
- Track playback works like normal music playback once the track is visible in the current folder.
- Recursive whole-tree actions such as full-tree `Play All`, full-tree `Shuffle`, and `Add entire folder tree to playlist` are not built yet.

### If Folders is missing or empty

1. Confirm the server build actually supports physical folder browsing.
2. Confirm the indexed music really exists in that server folder path.
3. Confirm the current user has permission to see that content.
4. Pull down to refresh the current folder view.

## Search

Search finds artists, albums, and tracks.

### How to use it

1. Open `Search`.
2. Type an artist, album, or track name.
3. Wait for results.
4. Read results in this order: Artists, Albums, Tracks.
5. Tap an artist to open Artist Detail.
6. Tap an album to open Album Detail.
7. Tap `Play` on a track to start playback from the Tracks results.
8. Use the clear icon in the search box to remove the current text.
9. When the search box is empty, tap a recent search to run it again.
10. Tap `Clear` beside Recent Searches to remove the recent search list.
11. Swipe down from the top of Search to rerun the current search without changing the text.

### Note

- Recent searches are saved only after a search returns results.
- Starting a track from Search creates a queue from the Tracks results.
- Next and previous follow the Tracks results queue after playback starts.
- Search track rows include the vertical three-dot song menu for adding that song to a playlist.

### If search has no results

- Try an exact name from Navidrome.
- Confirm the saved connection works in Settings.
- Confirm the phone can reach the server.

## Album Detail And Starting Playback

Album Detail shows the tracks for one album and starts album playback.

### How to use it

1. Open an album from Home, Library, Artist Detail, or Search.
2. Tap `Play Album` to start at track one.
3. Tap a specific track row to start at that track.
4. Watch the mini-player appear at the bottom of the screen.
5. Open `Playing` for full controls and queue editing.
6. Use the vertical three-dot menu on a track row to add that track to a playlist.
7. Use the vertical three-dot menu near the album controls to add the full album to a playlist.
8. Use the album menu to download the full album to Cirque's app-private Music downloads.

### Note

- If you start from a middle track, Cirque still builds the full album queue.
- The current track is highlighted.
- Track numbers and durations appear when the server provides them.

### Add a song to a playlist

1. Find a song in Album Detail, Playlist Detail, Library Songs, Library Favorites, or Search Tracks.
2. Tap the vertical three-dot menu on the song row.
3. Tap `Add to playlist`.
4. To create a new playlist, enter a new playlist name and tap `Create Playlist`.
5. To use an existing playlist, find it in the Existing playlists list and tap `Add`.
6. Read the success or error message.

The existing playlist option appends the selected song to the playlist on Navidrome.

### Add an album to a playlist

1. Find an album on Home, Library Albums, Artist Detail, Search Albums, or Album Detail.
2. Tap the vertical three-dot menu on the album tile, album row, or Album Detail header.
3. Tap `Add album to playlist`.
4. To create a new playlist from the album, enter a new playlist name and tap `Create Playlist from Album`.
5. To add the album to an existing playlist, find the playlist in the Existing playlists list and tap `Add`.
6. Read the success or error message.

Cirque adds the album tracks in album order. The existing playlist option appends those tracks after the playlist's current tracks.

### Download an album

1. Find an album on Home, Library Albums, Artist Detail, Search Albums, or Album Detail.
2. Tap the vertical three-dot menu on the album tile, album row, or Album Detail header.
3. Tap `Download album`.
4. Confirm the number of tracks shown.
5. Tap `Download`.
6. Wait for the progress and completion message.

Album files are saved under Cirque's app-private Music downloads on the phone. Android does not need a broad storage permission for this location. After the download completes, open `Library` > `Downloads` to play the album offline or remove the local files.

### Download a playlist

1. Open `Library`.
2. Tap `Playlists`.
3. Tap the vertical three-dot menu on a playlist row or grid item, or open Playlist Detail and use the playlist menu near the title.
4. Tap `Download playlist`.
5. Confirm the number of tracks shown.
6. Tap `Download`.
7. Wait for the progress and completion message.

Playlist files are saved under Cirque's app-private Music downloads on the phone. After the download completes, open `Library` > `Downloads` to play the playlist offline or remove the local files.

### Remove a track from a playlist

1. Open `Library`.
2. Tap `Playlists`.
3. Open the playlist you want to edit.
4. Tap the vertical three-dot menu on the track row.
5. Tap `Remove from playlist`.
6. Confirm `Remove`.
7. Wait for the playlist to reload.

Cirque removes the selected occurrence of the track. If the same song appears more than once in the playlist, only the selected row is removed.

## Mini-Player

The mini-player is the compact control bar at the bottom of the app.

### How to use it

1. Tap play/pause to pause or resume.
2. Tap stop to stop playback and clear the active queue.
3. Tap artwork or track text to open Playing.
4. Swipe right for next track.
5. Swipe left for previous track.

### Note

- The mini-player shows artwork, title, subtitle, loading state, and progress when available.
- It avoids showing raw server URLs in normal connected state.

## Playing Screen

Playing is the full playback control screen.

### How to use it

1. Open `Playing` from the bottom navigation, or tap the mini-player artwork/text.
2. Use play/pause to pause or resume.
3. Use stop to stop playback and clear the active queue.
4. Use previous and next to move through the queue.
5. Drag the seek slider to move within the current track.
6. Use elapsed and remaining time to understand track position.
7. Swipe right for next track.
8. Swipe left for previous track.
9. Scroll to `Up Next` to work with the queue.

### Note

- Stop clears the current queue.
- Previous and next follow the current queue, shuffle, and repeat settings.
- Album, playlist, search track-result, Songs, and Favorites playback build queues.
- Song row menus can add one song to a new or existing playlist without replacing the current queue.
- Album menus can add a full album to a new or existing playlist without replacing the current queue.
- Album and playlist menus can download their tracks to Cirque's app-private Music downloads.
- Playlist track menus can remove the selected track from the current playlist.
- On Android TV, Playing includes a `Dark Screen` button that blanks the TV while music continues. Press any remote button or click/tap the screen to return to the normal Playing view.

## Queue, Shuffle, And Repeat

The `Up Next` queue appears on the Playing screen.

### Queue editing

1. Start an album or playlist.
2. Open `Playing`.
3. Scroll to `Up Next`.
4. Tap a queue item to jump to it.
5. Tap `Up` to move an item earlier.
6. Tap `Down` to move an item later.
7. Tap `Remove` to remove an item.
8. Type a playlist name under `Save Queue`.
9. Tap `Save Queue as Playlist` to save the current queue back to Navidrome.

If you remove the only remaining item, playback stops and the queue is cleared.

### Save queue as playlist

1. Start playback from an album, playlist, search result, Songs, or Favorites.
2. Open `Playing`.
3. Scroll to `Save Queue`.
4. Enter a playlist name.
5. Tap `Save Queue as Playlist`.
6. Wait for the success or error message.

The saved playlist is created on the connected Navidrome server for the current account.

### Shuffle

1. Open `Playing`.
2. Tap `Shuffle Off`.
3. Confirm it changes to `Shuffle On`.
4. Tap again to turn shuffle off.

### Repeat

1. Open `Playing`.
2. Tap `Repeat Off`.
3. Tap again for `Repeat All`.
4. Tap again for `Repeat One`.
5. Tap again to return to `Repeat Off`.

### Queue restore

Cirque saves queue items, current index, approximate position, shuffle, and repeat. If playback is recreated, Cirque restores the queue. Position restore is approximate because it is saved periodically.

## Download Network And Storage Settings

Cirque can protect against accidental mobile-data downloads and excessive local storage use.

### Network rule

`Wi-Fi only` is the default. With this setting, Cirque starts downloads only when Android reports the active network as Wi-Fi or Ethernet. If the phone is on mobile data, the download is blocked with a clear message.

`Wi-Fi + phone data` allows downloads on either Wi-Fi or mobile data. Use this only if your phone plan and data allowance are suitable.

### Storage limit

The storage limit is the maximum app-private download storage Cirque should use for downloaded albums and playlists.

How to change it:

1. Open `Settings`.
2. Tap `Offline & Downloads`.
3. Find `Downloads`.
4. Review `Used`, `Limit`, and `Available on device`.
5. Enter a new limit in MB.
6. Start the download again.

### Note

- Cirque stores downloads in its app-private Music folder.
- Android removes this app-private storage if Cirque is uninstalled.
- The storage limit is checked before and during downloads.
- If the limit is reached, remove downloaded items from `Library` > `Downloads` or increase the limit in Settings.
- The available-space number comes from Android storage available to Cirque, not a separate public Downloads folder.

## Streaming Quality

Streaming mode controls what Cirque asks Navidrome to send.

### Original

Use `Original` when you want the source file from Navidrome.

Recommended for:

- Best quality.
- Home Wi-Fi.
- Wired audio.
- High-quality Bluetooth.
- Avoiding unnecessary server-side transcoding.

### Transcode MP3

Use `Transcode MP3` when you want Navidrome to send 192 kbps MP3.

Useful for:

- Slower networks.
- Compatibility with source formats that do not play reliably.
- Reducing bandwidth.

Transcoding may increase startup delay because the server may need to convert the file.

### How to change streaming mode

1. Open `Settings`.
2. Tap `Playback`.
3. Find `Streaming`.
4. Tap `Original` or `Transcode MP3`.
5. Confirm the active button is highlighted and says `Active`.

## Background Playback And System Controls

Cirque uses a Media3 service-backed player. This allows playback to continue outside the foreground screen and provides the foundation for Android media controls.

### How to test it

1. Start playback in Cirque.
2. Leave the app.
3. Confirm playback continues.
4. Pull down notifications and look for media controls.
5. Lock the phone and check lock-screen controls.
6. Try play, pause, next, and previous from system controls.
7. Disconnect headphones or Bluetooth and confirm playback pauses.

### Android Auto artwork

- Cirque sends track artwork to Android Auto through Android's media metadata system.
- Cirque now also embeds a small downscaled artwork image in playback metadata where possible, so compact split-screen cards do not have to rely only on fetching the cover from the server.
- Android Auto still controls the final layout. Some car screens may hide artwork in the smallest split-screen tile even when Cirque has supplied it.

### If controls are missing

- Allow notification permission if Android asks.
- Start playback from inside Cirque first.
- Check Android battery restrictions for Cirque.
- Re-test after reinstalling the latest APK.

## Bluetooth Audio

Cirque uses Android's normal media audio path. Android, the phone hardware, and the audio device negotiate the Bluetooth codec.

### How to get best quality

1. Set Streaming to `Original`.
2. Use headphones or speakers that support the codec you want.
3. Play a track in Cirque.
4. Use Android Developer Options if you want to inspect the negotiated codec.

Common codecs include SBC, AAC, aptX, aptX HD, aptX Adaptive, LDAC, and LC3 / LE Audio.

Cirque does not need its own Bluetooth codec switch.

## Pulse

Pulse is an optional listening-recap feature powered by the Navidrome Pulse plugin. It is not part of standard Navidrome or the normal Subsonic API. Cirque hides Pulse when the Pulse data playlist is missing or when the plugin has not generated a usable snapshot yet.

### What Pulse can show

Pulse can show weekly, monthly, and yearly recaps, depending on what periods are enabled in Settings > Pulse and what the plugin has generated.

Current Cirque Pulse cards can include:

- total listening minutes and plays
- top artists, tracks, albums, genres, and moods
- listening habits such as peak day, favourite time, weekday/weekend split, dayparts, and active hours; the breakdown numbers are total listening minutes, not play counts or percentages
- listening shape such as variety score, repeat ratio, and top artist/album/genre concentration
- library recency, including newer additions versus long-owned tracks
- session counts, average session length, longest session, and days listened
- podcast listening when the plugin provides podcast episode/minute data
- top podcast channels when the plugin provides channel counts
- podcast player breakdown when Pulse v0.1.6 or newer provides named-player counts
- podcast by time-of-day when the plugin provides `podcast_by_daypart`
- AI tag and My Tag breakdowns when the plugin provides tag play counts
- mood, AI tag, and My Tag by time-of-day cards when the plugin provides grouped daypart fields
- source breakdown when the plugin provides `source_breakdown` or the older `sources` map
- source by content type when the plugin provides `source_by_content_type`
- comparison insights when Cirque can read the previous snapshot for the same period

### Podcast and tag insight behavior

Podcast, podcast player, daypart, source/content, AI tag, and My Tag cards are conditional. They appear only when the Pulse snapshot contains the relevant fields. If you run an older Pulse plugin, these cards remain hidden rather than showing blank sections. Cirque now sends a lightweight `nd_source` value for playback attribution: normal scrobbles carry it through the durable pending-scrobble queue, and remote podcast episode streams append it to the stream URL. Standard Navidrome ignores this extra value; navidrome-experimental and the Pulse plugin must read it before source/device cards can show Phone, Android Auto, Android TV, or Tablet breakdowns.

Podcast Listening compares podcast time with total listening time, shows episode count, formats podcast minutes as hours/minutes, lists top podcast channels, can show podcast players such as Car, Phone, or Desktop, and can show podcast listening by time of day when the plugin provides those counts.

AI Listening Themes and Your Tag Patterns use the same ranked item shape as moods and genres. They turn tag counts into readable summaries instead of only listing raw numbers. Newer Pulse snapshots can also show how moods, AI tags, and My Tags change across morning, afternoon, evening, and night.

### Comparison insights

When the Pulse payload contains a previous snapshot for the same period type, Cirque adds a comparison card. It can compare listening time, podcast time, mood changes, variety score, and leading tag changes. If there is no previous snapshot, the comparison card is hidden.

### If Pulse is missing

1. Confirm the Pulse plugin is installed and enabled on the Navidrome server.
2. Confirm the plugin has written the `Pulse-Data` playlist.
3. Play music and wait for the plugin scheduler to generate a snapshot.
4. Use Demo Data in the plugin if you need an immediate display test.
5. Refresh Pulse in Cirque.
## Donationware

Cirque is donationware. Donations are optional and support development.

### Donation links

- $5 - Buy me a coffee: https://paypal.me/RFLundgren/5?app=cirque
- $10 - Buy me lunch: https://paypal.me/RFLundgren/10?app=cirque
- You decide, any amount: https://paypal.me/RFLundgren?app=cirque

### Note

The `app=cirque` parameter is a best-effort attribution hint. PayPal may ignore or remove custom parameters, so attribution still needs real-world verification.

## Troubleshooting

### Albums do not appear

1. Open Settings.
2. Confirm the saved connection says `Connection saved`.
3. Tap `Test Connection` if you changed server details.
4. Open the same address, port, and HTTP/HTTPS combination in the phone browser.
5. Confirm Navidrome has albums.
6. Return to Home or Library.

### Auto-detect does not find the server

1. Confirm the phone and server are on the same Wi-Fi.
2. Confirm the Port field matches the local Navidrome port.
3. Confirm the selected `HTTP` or `HTTPS` option matches the local server.
4. Confirm local access is not blocked by firewall rules.
5. Use manual entry for Tailscale, VPN, domains, reverse proxies, internet-hosted servers, or routes outside the current local subnet.

### Password disappears after saving

This is expected. Cirque stores token/salt credentials, not the raw password. Re-enter the password only when changing or recreating the connection.

### Feature seems missing after installing

1. Confirm the launcher app says `Cirque`.
2. Confirm About shows package `com.cirque.music`.
3. Confirm About shows the expected debug version.
4. Restart Cirque.
5. If the old prototype is installed, uninstall `com.navidromestreamer`.

### Playback does not start

1. Confirm the saved connection works.
2. Try another track or album.
3. Set Streaming to `Original`.
4. If Original fails, try `Transcode MP3`.
5. Confirm the phone has network access to the server.

### Download is blocked

1. Open `Settings`.
2. Tap `Offline & Downloads`.
3. Find `Downloads`.
4. If the message mentions Wi-Fi, connect to Wi-Fi or choose `Wi-Fi + phone data`.
5. If the message mentions storage, remove downloaded albums/playlists or increase the storage limit.
6. Try the download again.

### Library only shows Downloads

1. Open `Settings`.
2. Find `Offline Mode`.
3. Select `Online Library`.
4. Return to `Library`.

If Offline Mode is enabled, Library intentionally opens to Downloads and does not load live server sections.

### Queue looks wrong

1. Tap stop.
2. Start the album again.
3. Open Playing.
4. Confirm `Up Next` shows the expected album tracks.
5. Use `Up`, `Down`, and `Remove` to adjust the queue.

### Artwork does not appear

1. Confirm artwork appears in Navidrome.
2. Confirm the phone can reach the server.
3. Try another album.
4. If artwork is missing, Cirque should show a letter fallback.

## What Is Still Planned

Phone work still planned:

- Friendlier error messages.
- Notification and lock-screen polish.
- Release packaging.
- Podcast settings are still not built yet:
  - newest episodes count
  - show newest feed
  - episode sort order
- Recursive folder actions are still not built:
  - full-tree `Play All`
  - full-tree `Shuffle`
  - `Add entire folder tree to playlist`

Future device work:

- Tablet-specific layouts.
- Android Auto expansion for Podcasts and Folders.
- Android TV polish and broader large-screen refinement.

## Project Tracking

Project tracking now lives in:

- `planned-roadmap.md`: active short-form roadmap for current Android work.
- In-app `Release Notes`: user-facing summary of completed changes by version.

Update the roadmap and release notes after meaningful build or test cycles.
