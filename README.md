# Cirque Android Release

Cirque is a dedicated Android music client for Navidrome and compatible Subsonic API servers. It is built for people who want a fast self-hosted music app with strong offline playback, Android Auto support, Android TV listening support, theming, audio profiles, smart mixes, podcasts, folders, and richer server-backed insights where available.

Cirque is not open source. It is currently shared for testing and is planned as donationware when it is ready for wider public use.

## Current Download

- Current APK: [downloads/cirque-0.1.101.apk](downloads/cirque-0.1.101.apk)
- Convenience copy: [downloads/cirque-latest.apk](downloads/cirque-latest.apk)
- Version: `0.1.101`
- Package: `com.cirque.music`
- Build type: release APK
- Android minimum SDK for dexing: 26

If Android warns that the app came from an unknown source, allow installation from your browser or file manager, then install the APK again.

## Server Compatibility

Cirque works with standard Navidrome for the core Subsonic music-client experience. Some newer areas are only visible when the connected server advertises the required experimental endpoints.

### Works With Standard Navidrome

- Connection profiles
- Local, VPN/Tailscale, domain/HTTPS, and custom connection styles
- Albums, artists, songs, playlists, favorites, and search
- Playback, queue, shuffle, repeat, and resume
- Artwork where Navidrome provides cover art
- Offline album and playlist downloads to the phone
- Android media notification and lock-screen controls
- Android Auto core playback and downloaded playlist playback
- Themes, accent color, and display settings
- Audio profile setup and EQ band controls inside the app

### Requires Navidrome Experimental Or Companion Plugins

These features are optional. Cirque probes the server and hides unsupported sections rather than breaking against a standard Navidrome server.

- Podcasts require the podcast Subsonic extension in the server.
- Folders require the physical-folder browsing extension in the server.
- AI Tags and My Tags require the experimental tag endpoints.
- AI tag category browsing for Genre, Language, and Mood requires experimental tag data.
- Skipped/disliked track indicators require server-side skip metadata support.
- Pulse dashboards require the Pulse plugin/data path.
- Deeper AI playlist and mood workflows require the relevant companion plugins.

Experimental repositories:

- Navidrome experimental fork: [RFLundgren/navidrome_experimental](https://github.com/RFLundgren/navidrome_experimental)
- AI auto tagging plugin: [RFLundgren/AI-auto-tagging-plugin](https://github.com/RFLundgren/AI-auto-tagging-plugin)
- AI mood playlists plugin: [RFLundgren/AI-Mood-Playlists-Plugin](https://github.com/RFLundgren/AI-Mood-Playlists-Plugin)
- Pulse: [RFLundgren/pulse](https://github.com/RFLundgren/pulse)

## First Test Checklist

1. Install the APK.
2. Open Cirque.
3. Add a connection profile for your server.
4. Tap `Test Connection` before saving.
5. Open Library and confirm albums, artists, songs, and playlists load.
6. Start playback and confirm notification controls appear.
7. Download a small playlist and confirm it appears under Library > Downloads.
8. If using Android Auto, start from downloaded playlists or normal playlists and test playlist switching.
9. If using the experimental server, confirm Podcasts, Folders, AI Tags, My Tags, skipped tracks, and Pulse appear only where your server supports them.

## Documentation

- Full user help: [HELP.md](HELP.md)
- Release notes: [RELEASE_NOTES.md](RELEASE_NOTES.md)
- Privacy note: [PRIVACY.md](PRIVACY.md)
- Third-party notices: [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)
- Checksums: [SHA256SUMS.txt](SHA256SUMS.txt)

## Feedback

Please include the Cirque version, Android device, Android version, server version, connection type, and whether you are using standard Navidrome or the experimental fork when reporting problems.
