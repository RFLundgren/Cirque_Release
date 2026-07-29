# Cirque Release Notes

## 0.1.101

This release refreshes the public test APK in the Cirque_Release repository. The APK is distributed directly from the repository downloads folder rather than a GitHub Release, because GitHub Releases automatically expose source archives that are confusing for a closed-source app.

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

### Pulse And Source Attribution

- Pulse cards now support newer optional plugin fields for podcasts, podcast players, AI Tags, My Tags, comparison insights, source/device breakdowns, playback-origin breakdowns, streamed/downloaded breakdowns, source/origin matrix patterns, and source-by-content summaries.
- Pulse Overview now includes a richer `How You Listen` card when attribution fields are present, using friendly labels such as Phone, Android Auto, Playlist, Smart Mix, Streamed, and Downloaded.
- Pulse Story now includes a `Your Listening Map` card when attribution data is available.
- Listening Habits now labels weekday/weekend, daypart, and active-hour values as total listening minutes rather than play counts.
- Cirque sends lightweight `nd_source`, `nd_origin`, and `nd_playback_mode` hints for normal music scrobbles, and `nd_source` for remote podcast episode stream URLs.
- Source values currently include `android_phone`, `android_tablet`, `android_tv`, and `android_auto`; origin values include album, artist, playlist, search, smart mix, queue, and radio; playback modes are streamed and downloaded.
- Standard Navidrome ignores these additive parameters. navidrome-experimental `develop` and a compatible Pulse plugin must read/store/aggregate them before attribution cards appear; this newer Pulse attribution surfacing is not available in the current `stable` channel.

### Experimental Server Features

These features require Navidrome experimental support or companion plugins and are hidden when unsupported:

- `stable` and `develop`: Podcasts.
- `stable` and `develop`: Physical folder browsing.
- `stable` and `develop`: Base enhanced attribution where available. Newer Pulse source/device, origin, playback-mode, and source/origin matrix cards require `develop`.
- `develop` only: User-defined song tagging.
- `develop` only: AI Tags, AI Genre, AI Mood, and My Tags dashboards.
- `develop` only: Skipped/disliked track indicators and server-side skip behavior.
- `develop` only: Genre exploration and genre merging benefits.
- Plugin-backed: Pulse insight cards require Navidrome plugin support, documented by Pulse as a Navidrome build dated 2026-03-03 or later, plus the Pulse plugin.
- Plugin-backed: AI tagging and AI mood playlist workflows.

### Known Limits

- Some Android Auto split-screen layouts may still hide artwork even when metadata is provided.
- Recursive folder actions are not yet implemented.
- Podcast settings are still early.
- Advanced audio tuning is staged; full parametric EQ, compression, loudness, and device-assigned profiles remain planned.
- Pulse source/device, origin, playback-mode, and source/origin matrix cards only appear after a compatible navidrome-experimental `develop` and Pulse plugin stack emits the matching snapshot fields.
