# Helix League Scoreboard Broadcast Package

A fully separated, cloud-synchronized broadcast graphics package built for sports streaming and OBS integration.

## Architecture

This graphics package is split into two independent files that synchronize automatically over the internet using **Google Firebase Realtime Database**:

1. **`control_center.html`**: The master dashboard used by the broadcast operator to update scores, trigger player graphics, and manage the game clock.
2. **`goal_bar.html`**: The broadcast overlay (Scorebug, Player Lower Thirds, Tickers) meant to be ingested into OBS or vMix as a Browser Source.

### Features
* **Zero-Setup Real-time Sync**: Firebase Realtime Database is pre-configured to sync state across devices instantly.
* **Separated UI**: Keep your control panel on a separate monitor or completely different laptop from your broadcasting PC.
* **Dynamic Player Graphics**: Trigger lower thirds for Goals, Yellow/Red Cards, and Man of the Match.
* **Animated Stream Overlays**: Smooth tickers and animated sponsors out-of-the-box.
* **React + Tailwind**: Fully styled with TailwindCSS and powered by React (no build step required).

## How to Use (OBS Setup)

1. **Open the Control Center**
   - Open `control_center.html` in any modern web browser.
   
2. **Add to OBS**
   - In OBS (or vMix), add a new **Browser Source**.
   - Check the box for "Local File" and select `goal_bar.html`.
   - Set the dimensions to your canvas size (recommended: **Width: 1920**, **Height: 1080**).
   - *Note: Keeping the source at 1920x1080 ensures all elements (top scorebug, bottom ticker, etc.) are positioned perfectly.*

3. **Operate the Match**
   - Use the `control_center.html` interface to increment scores, start/stop the clock, and trigger goal alerts. All changes will push to your OBS overlay instantly via Firebase.

## Customization

To add or modify teams, sponsors, or player rosters, simply open `control_center.html` and `goal_bar.html` in a text editor and modify the `NATION_OPTIONS` and `SPONSOR_OPTIONS` constants at the top of the script.

## Dependencies

This package runs entirely in the browser without a local server. It uses CDNs for:
* Tailwind CSS
* React 18 & ReactDOM
* Babel (Standalone)
* Firebase 12.15.0 SDK
