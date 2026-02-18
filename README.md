# SmartMonitor — Smart Crowd Monitoring Dashboard

A real-time, browser-based crowd monitoring dashboard that tracks occupancy levels, visualizes trends, and triggers alerts when crowd thresholds are exceeded. Built with vanilla HTML, CSS, and JavaScript using Chart.js.

---

## Features

### 📊 Live Monitoring
- Fetches crowd data every 5 seconds from a backend API (`https://project-8eg3.onrender.com/api/dashboard`)
- Displays current crowd count and status (Normal / Moderate / Crowded)
- Live line chart showing the last 20 data points
- Hourly bar chart showing average crowd levels per hour of the day

### 🔔 Alert System
- In-app alert banners triggered when crowd status changes (Normal → Moderate → Crowded)
- Floating push notification badge with auto-dismiss (5 seconds)
- Sound alerts via the Web Audio API (distinct tones for normal, warning, and danger states)
- Voice announcements via the Web Speech API

### 📈 Statistics & Insights
- Tracks total entries and exits
- Calculates running average and peak crowd count
- Identifies peak and quietest hours
- Smart insights panel with trend detection (increasing / decreasing crowd) and capacity usage warnings

### 💾 Data Management
- Export all activity and hourly summary data to CSV
- Reset all data with confirmation prompt
- Pause and resume monitoring

### 🎨 UI & Theming
- Dark mode (default) and light mode with smooth transitions
- Theme preference persisted via `localStorage`
- Responsive layout using CSS Grid
- Animated navigation bar with scroll-aware active link highlighting

---

## Getting Started

This is a static frontend — no build tools or dependencies to install. Simply open `index.html` in a browser.

```bash
# Clone the repo
git clone <your-repo-url>
cd <project-folder>

# Open in browser
open index.html
```

> **Note:** The dashboard fetches data from `https://project-8eg3.onrender.com/api/dashboard`. Make sure this backend is running and accessible, or update the URL in the `updateDashboard()` function to point to your own API.

---

## Backend API

The frontend expects a `GET` endpoint at `/api/dashboard` that returns JSON in the following shape:

```json
{
  "deviceCount": 42
}
```

| Field         | Type   | Description                          |
|---------------|--------|--------------------------------------|
| `deviceCount` | number | Current number of people/devices detected |

---

## Configuration

Key thresholds and settings can be adjusted in the `settings` object in the `<script>` block:

```js
let settings = {
  updateInterval: 5000,       // Polling interval in ms
  moderateThreshold: 50,      // Crowd count that triggers "Moderate" status
  crowdedThreshold: 80,       // Crowd count that triggers "Crowded" status
  maxCapacity: 100            // Used to calculate capacity usage in insights
};
```

---

## Sound & Notification Controls

Users can configure alert behavior directly in the UI:

| Control               | Description                                      |
|-----------------------|--------------------------------------------------|
| 🔊 Sound Alerts        | Toggle Web Audio API beeps on/off               |
| 🗣️ Voice Announcements | Toggle Web Speech API announcements on/off      |
| 🔔 Push Notifications  | Toggle the floating notification badge on/off   |
| Volume Slider         | Adjusts master volume for sound and voice       |
| Test Sound Button     | Fires a test beep, voice message, and notification |

All settings are persisted via `localStorage`.

---

## Dependencies

| Library    | Version  | Source                                      |
|------------|----------|---------------------------------------------|
| Chart.js   | Latest   | `https://cdn.jsdelivr.net/npm/chart.js`     |

No package manager or bundler required.

---

## Browser Compatibility

Requires a modern browser with support for:
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)
- [Web Speech API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Speech_API)
- Fetch API
- CSS Grid & Custom Properties

Tested on Chrome and Edge. Firefox has limited Web Speech API support.

---

## Project Structure

```
index.html        # Single-file app — all HTML, CSS, and JS included
README.md         # This file
```

---

## License

MIT — free to use and modify.
