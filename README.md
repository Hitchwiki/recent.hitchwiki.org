# recent.hitchwiki.org

A real-time web application that displays HitchNotes from Nostr relays on an interactive map and timeline.

## Features

- **Real-time Updates**: Live connection to Nostr relays for instant note updates
- **Interactive Map**: Displays geo-located notes using Leaflet maps
- **Multiple Note Types**: Supports profiles, text notes, and hitchhiking trip data
- **Geo Information**: Extracts coordinates from geohash, Plus Codes, and trip data
- **Raw Data View**: Click on note types to view complete Nostr event data
- **Live Statistics**: Real-time count of total notes and geo-located notes

## Technology Stack

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Mapping**: Leaflet.js
- **Protocol**: Nostr (decentralized social protocol)
- **Styling**: Custom CSS with gradient themes

## Supported Note Types

- **Kind 0**: User profiles with metadata
- **Kind 1**: Text notes with images and hashtags
- **Kind 36820/443**: Hitchhiking trip data with coordinates
- **All other kinds**: Displayed with fallback rendering

## Geo Data Sources

The application extracts location information from:
- **Geohash tags** (NIP-52)
- **Open Location Codes** (Plus Codes)
- **Hitchhiking trip data** (JSON coordinates)
- **Content parsing** (decimal and degree coordinates)

## Relays

Currently connects to:
- `wss://relay.hitchwiki.org`
- `wss://relay.trustroots.org`

## Usage

1. Open `htdocs/index.html` in a web browser
2. The app automatically connects to Nostr relays
3. Notes appear in real-time in the list view
4. Geo-located notes are plotted on the map
5. Click on note type tags to view raw Nostr data

## Development

The application uses persistent WebSocket connections to maintain real-time updates. New notes are automatically added to the top of the list and plotted on the map if they contain geo information.

## License

This project is part of the HitchWiki ecosystem for the hitchhiking community.