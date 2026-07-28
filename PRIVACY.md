# Cirque Privacy Note

Cirque is a self-hosted music client for Navidrome/Subsonic servers.

## Data Cirque Stores On The Device

Cirque stores the information needed to connect to your server:

- Server URL and port
- Connection profile name
- Username
- Navidrome/Subsonic token and salt
- Playback and display preferences
- Recent searches
- Offline download metadata
- Playback queue state
- Downloaded audio files that you choose to save for offline playback

Cirque does not store your server password directly after a successful save. It stores the token and salt needed for Navidrome/Subsonic authentication.

## Data Sent To Your Server

Cirque sends requests to the Navidrome/Subsonic server that you configure. Those requests include normal music-client actions such as browsing, searching, streaming, downloading, starring, playlist editing, and scrobbling play progress.

## Donations

Donation links open PayPal in a browser or PayPal app. PayPal processes that transaction. Cirque does not receive payment card details.

Donation links include a best-effort `app=cirque` attribution parameter. PayPal may remove or ignore that parameter, so attribution is not guaranteed.

## Third Parties

Cirque does not include analytics, advertising, or tracking SDKs.

Cirque uses open-source Android libraries listed in `THIRD_PARTY_NOTICES.md`.

## Offline Downloads

Downloaded music is stored in Cirque's app-private storage area. Removing the app may remove those files. Use the in-app Downloads controls to remove downloaded albums and playlists when you no longer need them.

## Current Build Status

This is an early phone-focused build. Tablet, Android Auto, and Android TV support are still in progress.
