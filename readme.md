# Boost Your Country — YouTube Live Overlay

A mobile-first browser overlay inspired by the supplied Prism Live design. It can be loaded as a browser/web source in a streaming app such as PRISM Live.

## What is included
- Country flags + live points + 1/2/3 podium
- Chat country vote → +10 points per valid country vote
- Super Chat → 40,000 points per $1
- Member event → 400 points
- Like/subscriber increases → 400 points per detected increase, assigned to the selected country
- Goal in dollars
- Supporter list
- Live chat display
- Sound effects for events
- Settings/admin panel
- Netlify serverless function for YouTube Data API
- Local persistence of points/settings

## Important YouTube API limitations
YouTube Live Chat does not provide the viewer's country automatically. This build therefore detects a country flag emoji or a country name/alias written in the chat (for example `🇲🇦`, `Morocco`, `maroc`, or `المغرب`) and awards +10 points to that country. The selected country is only a fallback for events that do not contain a country. YouTube's public subscriber count is rounded, so subscriber-event detection is an estimate based on changes in that count. Likes are read from the video's statistics. These behaviors follow the public YouTube API fields.

## Deploy to Netlify
1. Create a Google Cloud project and enable **YouTube Data API v3**.
2. Create an API key.
3. Upload this folder to a new Netlify site.
4. In Netlify → Site configuration → Environment variables, add:
   `YOUTUBE_API_KEY = your_key`
5. Open your Netlify URL on your phone.
6. Open Settings, paste your live/video URL, choose a default country, and tap **Connect Live**.
7. In PRISM Live, add a Web/Browser source using your Netlify URL.

For better security, keep the API key in Netlify environment variables rather than pasting it into the page. Restrict the Google API key to YouTube Data API v3 where possible.

## Notes
- The live chat API is only available while the live event exposes its live chat.
- The overlay is designed for portrait/mobile use but also works in a desktop browser.


## PRO Live Engine (upgraded)
This version adds a production-style portrait live overlay while preserving the original YouTube chat/stat integration:
- 9:16-friendly HUD with LIVE timer, round number and concurrent viewer count when YouTube exposes it.
- Animated battle banner and current-leader card with live lead gap/progress.
- Live activity feed for chat votes, Super Chats, members, likes and subscribers.
- Live points/vote/support metrics.
- Stronger motion, glow, depth, responsive cards and mobile-first spacing.
- Round controls and custom battle title/subtitle in Settings.
- Existing Netlify YouTube function now also returns `concurrentViewers` from `liveStreamingDetails` when available.

### Notes
YouTube does not provide a viewer's country as a normal live-chat field. Country voting still works by detecting a country flag/name/alias in the chat. Subscriber and like changes are detected by polling public statistics, so those events are estimates rather than an official per-user event stream.
