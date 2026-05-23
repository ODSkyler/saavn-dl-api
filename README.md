# Saavn Downloader API

Ultra-lightweight JioSaavn song metadata API built for downloaders, streamers and music apps.  
Currently being used by saavn-dl.pages.dev and saavn.squid.wtf

No bloated wrappers.  
No useless modules.  
Just clean song data.

---

## Features

- Extracts song metadata from JioSaavn URLs
- Clean JSON response
- High-quality 500x500 artwork
- Artist + album parsing
- Song preview URL support
- Encrypted media URL extraction
- Permanent CDN link after decryption
- Cloudflare Worker based
- Extremely fast
- Frontend friendly
- CORS enabled

---

## Example

### Input

```txt
https://www.jiosaavn.com/song/blinding-lights/Fj9GfAxDWUY
```

### Endpoint

```txt
https://sda.rhythmax.workers.dev/song?url=https://www.jiosaavn.com/song/blinding-lights/Fj9GfAxDWUY
```

---

## Example Response

```json
{
  "id": "fW-Mxsnu",
  "token": "Fj9GfAxDWUY",
  "title": "Blinding Lights",
  "subtitle": "The Weeknd - After Hours",
  "type": "song",
  "perma_url": "https://www.jiosaavn.com/song/blinding-lights/Fj9GfAxDWUY",
  "image": "https://c.saavncdn.com/077/After-Hours-English-2020-20240207070330-500x500.jpg",
  "language": "english",
  "year": "2020",
  "play_count": "36483136",
  "isExplicit": true,
  "more_info": {
    "album_id": "19531208",
    "album_token": "y0pOEMYQFWQ_",
    "album": "After Hours",
    "album_url": "https://www.jiosaavn.com/album/after-hours/y0pOEMYQFWQ_",
    "encrypted_media_url": "ID2ieOjCrwfgWvL5sXl4B1ImC5QfbsDyi/BLZu7e+Ua0SbPMHRYSGrRsUG6JhLOJ2PIigzqe+euc2PinCwWEMRw7tS9a8Gtq",
    "duration": "204",
    "copyright_text": "℗ 2019 The Weeknd XO, Inc., manufactured and marketed by Republic Records, a division of UMG Recordings, Inc.",
    "artists": {
      "primary": [
        {
          "id": "615155",
          "artist_token": "FJRb7GbYWrQ_",
          "name": "The Weeknd",
          "image": "https://c.saavncdn.com/artists/The_Weeknd_002_20241003071400_500x500.jpg",
          "perma_url": "https://www.jiosaavn.com/artist/the-weeknd-songs/FJRb7GbYWrQ_"
        }
      ],
      "featured": []
    },
    "release_date": "2020-03-20",
    "vcode": "010912291152065",
    "vlink": "https://jiotunepreview.jio.com/content/Converted/010912291108341.mp3"
  }
}
```

---

## Routes

Response:

### Fetch Song

```txt
GET /song?url=JIOSAAVN_URL
```

Example:

```txt
/song?url=https://www.jiosaavn.com/song/blinding-lights/Fj9GfAxDWUY
```

---

## Deployment

### 1. Clone

```bash
git clone https://github.com/ODSkyler/saavn-dl-api.git
cd saavn-dl-api
```

### 2. Install

```bash
npm install
```

### 3. Login to Cloudflare

```bash
npx wrangler login
```

### 4. Deploy

```bash
npm run deploy
```

---

## Note

- This API only returns metadata + encrypted media URL
- Decryption should be done on frontend/client
```bash
Use:
- DES
- ECB mode
- PKCS7 padding
- Key: 38346591
```
- Designed for saavn-dl

---

## Why?

Because most JioSaavn APIs on GitHub are
- abandoned
- bloated
- broken
- insanely slow

This one stays simple.

---

## Geo Restrictions

JioSaavn applies regional restrictions on some English and international songs/albums outside India due to licensing issues.
`Source: JioSaavn FAQ`

Since this API is hosted on Cloudflare's global network, requests may sometimes route through non-Indian regions. Because of this, English/international content may:
- not appear in results
- return incomplete metadata
- fail to resolve properly

Hindi and most Indian regional content usually work without issues.

This is a limitation from JioSaavn's side, so It's not my fault and not API bug. But I'm working on geo-restriction bypass so stay tuned!

---

## Disclaimer

This project is created strictly for educational and research purposes only.

All music content, trademarks, album arts, audio files and related assets belong to their respective owners, labels and artists.

`saavn-dl-api` does NOT:
- host music files
- store copyrighted content
- upload media
- distribute songs
- maintain any music database

The API simply fetches publicly accessible metadata and references already available on platform.

This project is intended for:
- learning purposes
- reverse engineering practice
- API experimentation
- home lab environments
- personal educational use

Piracy is illegal.  
Users are solely responsible for how they use this software.

---

## License

This project is licensed under MIT License

---

## Author

Made with ❤️ by OD Skyler
