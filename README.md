# 💧 Waterfall Explorer

A lightweight, mobile-ready web app for finding waterfalls near any
location, using live data from
[OpenStreetMap](https://www.openstreetmap.org) via the [Overpass
API](https://overpass-api.de). Works in any modern browser and can be
installed as a Progressive Web App (PWA) on both iPhone and Android.

---

## Features

- **Two search modes** — find waterfalls by proximity to parking areas, or by proximity to hiking trails
- **Adjustable parameters** — set the search radius, maximum parking distance, or maximum trail distance using sliders
- **Live map** — results displayed on an interactive OpenStreetMap base map with color-coded markers
- **Waterfall details** — hover or tap any marker to see the waterfall's name, height (when available), access distance, and a link to its location on OpenStreetMap
- **Flexible location setting** — type any place name, click anywhere on the map, or use your device's GPS to set the search center
- **Server failover** — automatically retries across four independent Overpass API servers if one is busy or unreachable
- **PWA support** — installable on iPhone (via Safari → Add to Home Screen) and Android (via Chrome → Add to Home Screen) for a full-screen, app-like experience

---

## Screenshots


---

## Usage

### Running locally

Download `index.html` and `manifest.json` to the same folder and open `index.html` in any modern browser (Safari, Chrome, Firefox). No build step, no dependencies to install — everything is self-contained.

> **Note:** The GPS "use my location" feature requires HTTPS and will not work when opening the file directly from disk (`file://`). All other features work locally.

### Hosted on GitHub Pages

1. Fork or clone this repository
2. Go to **Settings → Pages**
3. Set the source to the `main` branch, root folder
4. Your app will be live at `https://yourusername.github.io/waterfall-explorer/`

### Installing as a mobile app

**iPhone (Safari)**
1. Open the hosted URL in Safari
2. Tap the Share icon → **Add to Home Screen**
3. Tap **Add** — the app launches full-screen from your Home Screen

**Android (Chrome)**
1. Open the hosted URL in Chrome
2. Tap the menu (⋮) → **Add to Home Screen**, or wait for Chrome's install prompt
3. Tap **Install** — the app launches full-screen from your Home Screen

---

## How it works

Search parameters (location, radius, and access distance) are sent as a single optimized [Overpass QL](https://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL) query that fetches waterfalls and either parking areas or hiking trails in one round trip. Proximity calculations are done client-side using the Haversine formula. The map is rendered with [Leaflet](https://leafletjs.com).

### Waterfall marker colors

**Parking mode**
| Color | Meaning |
|-------|---------|
| 🔵 Blue | Waterfall with a parking area within the selected distance |
| ⚫ Dark grey | Named waterfall, no nearby parking |
| ⚪ Light grey | Unnamed waterfall, no nearby parking |

**Trail mode**
| Color | Meaning |
|-------|---------|
| 🟢 Green | Waterfall within the selected distance of a hiking trail |
| _(others hidden)_ | Waterfalls with no nearby trail are not shown |

---

## Files

| File | Description |
|------|-------------|
| `index.html` | The complete application (HTML, CSS, and JavaScript) |
| `manifest.json` | PWA manifest for Android home screen installation |
| `README.md` | This file |

---

## Data sources

All map and feature data is fetched live from [OpenStreetMap](https://www.openstreetmap.org) © OpenStreetMap contributors, licensed under the [Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/). Coverage of waterfalls, parking, and trails varies by region.

Geocoding (place name search) uses the [Nominatim](https://nominatim.openstreetmap.org) service.

---

## Requirements

A modern browser with JavaScript enabled. No server, no backend, no API keys required.

| Browser | Support |
|---------|---------|
| Safari (macOS / iOS) | ✅ Full support |
| Chrome (desktop / Android) | ✅ Full support |
| Firefox (desktop / Linux) | ✅ Full support |
| Internet Explorer | ❌ Not supported |

---

## Author

**Waterfall Explorer** was designed by the repository owner and coded by [Claude](https://claude.ai) (Anthropic), via an iterative conversation-driven development process.

Repository owner has manually examine this code and ascertained that it accesses only expected servers: Overpass servers for geographic queries, Openstreetmap for map and feature data, and unpkg.com (Open-source CDN) for access to Leaflet.

---

## License

This project is released under the [MIT License](https://opensource.org/licenses/MIT). You are free to use, modify, and distribute it for any purpose. Please retain attribution to the original authors.
