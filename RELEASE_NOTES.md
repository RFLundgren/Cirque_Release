# Cirque Release Notes

## 0.1.101

This is the first public test release published through the Cirque_Release repository. The APK is distributed directly from the repository downloads folder rather than a GitHub Release, because GitHub Releases automatically expose source archives that are confusing for a closed-source app.

### Core App

- Release APK published as `downloads/cirque-0.1.101.apk`.
- Device targets called out clearly: Android phones, Android tablets, Android Auto, and Android TV.
- Package name is `com.cirque.music`.
- Connection profiles allow switching between production, test, local, VPN/Tailscale, domain/HTTPS, and custom server setups.
- Automatic profile selection supports home network, away/VPN network, and mobile fallback routes.
- Theme, accent, custom color, display chip, and layout settings are available in Settings.
- Audio profile setup includes visible EQ band frequency labels and staged sound-tuning controls.
- Diagnostics and support bundle work has been expanded for better real-world troubleshooting.

### Playback And Offline

- Albums, artists, songs, playlists, favorites, search, queue, shuffle, repeat, and resume are available for normal Navidrome/Subsonic use.
- Offline album, playlist, and podcast episode download handling has clearer state and refresh behavior.
- Download network and storage protection are available in Settings.
- Android media notification and lock-screen controls are supported.
- Android Auto playback and downloaded playlist handling have been improved.
- Android Auto artwork metadata is supplied by Cirque, although the car host controls final compact layout behavior.
- Android TV includes an early dark listening screen option.

### Experimental Server Features

These features require Navidrome experimental support or companion plugins and are hidden when unsupported:

- `stable` and `develop`: Podcasts.
- `stable` and `develop`: Physical folder browsing.
- `stable` and `develop`: Enhanced scrobble attribution for richer Pulse/source context.
- `develop` only: User-defined song tagging.
- `develop` only: AI Tags, AI Genre, AI Mood, and My Tags dashboards.
- `develop` only: Skipped/disliked track indicators and server-side skip behavior.
- `develop` only: Genre exploration and genre merging benefits.
- Plugin-backed: Pulse insight cards require Navidrome plugin support, documented by Pulse as a Navidrome build dated 2026-03-03 or later, plus the Pulse plugin. Recaps can include top artists/tracks/albums/genres, moods, sessions, diversity, recency, and track obsession; enhanced source attribution is best with navidrome-experimental `stable` or `develop`.
- Plugin-backed: AI tagging and AI mood playlist workflows.

### Known Limits

- Some Android Auto split-screen layouts may still hide artwork even when metadata is provided.
- Recursive folder actions are not yet implemented.
- Podcast settings are still early.
- Advanced audio tuning is staged; full parametric EQ, compression, loudness, and device-assigned profiles remain planned.
