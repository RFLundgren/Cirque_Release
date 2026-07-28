# Cirque Release Notes

## 0.1.101

This is the first public test release published through the Cirque_Release repository. The APK is distributed directly from the repository downloads folder rather than a GitHub Release, because GitHub Releases automatically expose source archives that are confusing for a closed-source app.

### Core App

- Release APK published as `downloads/cirque-0.1.101.apk`.
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

- Podcasts.
- Physical folder browsing.
- AI Tags.
- My Tags.
- AI Tag category browsing for Genre, Language, and Mood.
- Skipped/disliked track indicators.
- Pulse insight cards.
- AI tagging and AI mood playlist workflows.

### Known Limits

- Some Android Auto split-screen layouts may still hide artwork even when metadata is provided.
- Recursive folder actions are not yet implemented.
- Podcast settings are still early.
- Advanced audio tuning is staged; full parametric EQ, compression, loudness, and device-assigned profiles remain planned.
