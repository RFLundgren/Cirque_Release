# Cirque Android Release

Cirque is a dedicated Android music client for Navidrome and compatible Subsonic API servers. It is built for people who want a fast self-hosted music app with strong offline playback, phone and tablet support, Android Auto compatibility, Android TV listening support, theming, audio profiles, smart mixes, podcasts, folders, and richer server-backed insights where available.

Cirque is not open source. It is currently shared for testing and is planned as donationware when it is ready for wider public use.

## Current Download

- APK: [downloads/cirque-0.1.101.apk](downloads/cirque-0.1.101.apk)
- Version: `0.1.101`
- Package: `com.cirque.music`
- Build type: release APK
- Android minimum SDK for dexing: 26

If Android warns that the app came from an unknown source, allow installation from your browser or file manager, then install the APK again.

## Device Compatibility

Cirque is built for Android and currently supports these device types:

- Android phones: primary supported experience.
- Android tablets: supported with the same core app experience, with tablet-specific layout polish still evolving.
- Android Auto: supported for safe in-car browsing and playback controls, including playlists and downloads.
- Android TV: supported for playback-focused listening, including an early dark listening screen option.

Android Auto and Android TV use host-controlled layouts, so they may not expose every visual setting or advanced app feature available on the phone/tablet app.

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

Important: not every experimental feature is available in every navidrome-experimental build. The `stable` tag is the safer checkpoint. The `develop` tag is where newer work appears first.

| Feature | Server channel | What Cirque uses it for |
| --- | --- | --- |
| [Podcast support](https://github.com/RFLundgren/navidrome_experimental/blob/master/PODCAST_PLAN.md) | `stable` and `develop` | Podcasts section, episode playback, server-side episode download state, phone episode downloads, and playlist add where supported. |
| [Physical folder browsing](https://github.com/RFLundgren/navidrome_experimental/blob/master/navidrome-folder-roadmap.md) | `stable` and `develop` | Folders section for navigating and playing music by disk layout. |
| [Enhanced scrobble attribution](https://github.com/RFLundgren/navidrome_experimental#enhanced-scrobble-attribution-pulse-integration) | `stable` and `develop` for base attribution; newer Pulse source/device cards require `develop` | Richer Pulse/source context when available to the server and plugins. |
| [Pulse insights](https://github.com/RFLundgren/pulse) | Navidrome with plugin support, build dated 2026-03-03 or later, plus the Pulse plugin. Newer source/device Pulse breakdowns require navidrome-experimental `develop` plus a compatible Pulse plugin. | Weekly, monthly, and yearly listening recaps in Cirque: top artists, tracks, albums, genres, moods, listening habits, sessions, diversity metrics, library recency, podcast insight fields, AI/My Tag patterns, comparison insights, source/device breakdowns where provided, and track obsession. |
| [User-defined song tagging](https://github.com/RFLundgren/navidrome_experimental#user-defined-song-tagging-experimental) | `develop` only | My Tags, tag filtering, tag-based playlist workflows, and plugin-facing tag data. |
| [AI Genre / AI Mood / My Tags dashboards](https://github.com/RFLundgren/navidrome_experimental#ai-genre--ai-mood--my-tags-dashboards-experimental) | `develop` only | Library dashboards for AI Genre, AI Mood, and My Tags, with visibility controlled by Cirque settings and server capability probing. |
| [On-demand plugin actions](https://github.com/RFLundgren/navidrome_experimental#on-demand-plugin-actions-experimental) | `develop` only | Plugin config actions on the server side, such as one-off validation or manual plugin runs. |
| [Skip / auto-pass disliked songs](https://github.com/RFLundgren/navidrome_experimental#skip--auto-pass-disliked-songs-experimental) | `develop` only | Dimmed/skipped track indicators in Cirque and automatic skip behavior where the server exposes it. |
| [Genre exploration](https://github.com/RFLundgren/navidrome_experimental#genre-exploration-experimental) | `develop` only | Richer genre browsing and genre-based mix/playlist entry points when exposed by the server. |
| [Genre merging](https://github.com/RFLundgren/navidrome_experimental#genre-merging-experimental) | `develop` only | Cleaner genre data from the server after scan-time merges. Cirque benefits through normal genre/tag browsing. |

Features marked `develop` only have not reached a tagged `stable` checkpoint yet. See [Getting navidrome-experimental](https://github.com/RFLundgren/navidrome_experimental#getting-navidrome-experimental) for what the two tags mean.

Experimental repositories:

- Navidrome experimental fork: [RFLundgren/navidrome_experimental](https://github.com/RFLundgren/navidrome_experimental)
- AI auto tagging plugin: [RFLundgren/AI-auto-tagging-plugin](https://github.com/RFLundgren/AI-auto-tagging-plugin)
- AI mood playlists plugin: [RFLundgren/AI-Mood-Playlists-Plugin](https://github.com/RFLundgren/AI-Mood-Playlists-Plugin)
- Pulse plugin and insight system: [RFLundgren/pulse](https://github.com/RFLundgren/pulse)


### Pulse Notes

Pulse is not part of the normal Subsonic API. It requires a Navidrome build with plugin support, currently documented by Pulse as a build dated 2026-03-03 or later, plus the Pulse plugin itself. It records scrobbles and writes generated insight snapshots to a `Pulse-Data` playlist. Cirque knows how to read that payload and render it as Pulse insight cards.

Pulse starts collecting from the point it is installed. It does not import historical listening from Last.fm or other services. After installation, play music normally and allow the plugin scheduler to run before expecting real cards to appear in Cirque.

Pulse can provide weekly, monthly, and yearly recaps including total plays, listening minutes, top artists, top tracks, top albums, top genres, mood breakdowns, peak listening day/time, weekday versus weekend split, hourly patterns, listening streak, session counts, longest session, variety score, repeat ratio, top artist/album/genre concentration, recent-addition listening, podcast/channel/player insight, AI/My Tag patterns, comparison insights, source/device breakdowns where the server/plugin provide them, and track obsession.

Mood breakdowns require mood playlists to exist on the server, either created manually or through the AI mood playlist/tagging workflow. Source/client attribution requires navidrome-experimental `develop` and compatible Pulse plugin support for Cirque source hints. Cirque sends lightweight `nd_source` values for music scrobbles and remote podcast episode streams; standard Navidrome ignores these extra parameters. Phone, Tablet, Android TV, and Android Auto source/device breakdowns are not available in the current `stable` navidrome-experimental channel.

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

