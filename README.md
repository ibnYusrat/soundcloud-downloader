# node-soundcloud-downloader
Download Soundcloud tracks with Node.js
```
npm install soundcloud-downloader
```

I couldn't find any packages that worked with a Discord bot I was working on so I created my own. 

### Usage
This package exposes a function that takes a Soundcloud URL and a Client ID as parameters, and returns a Promise 
that will return a readable stream containing the audio data. 
```javascript
const scdl = require('soundcloud-downloader')
const fs = require('fs')

const SOUNDCLOUD_URL = 'https://soundcloud.com/askdjfhaklshf'
const CLIENT_ID = 'asdhkalshdkhsf'

scdl(SOUNDCLOUD_URL, CLIENT_ID).then(data => data.pipe(fs.createWriteStream('audio.mp3')))
```

### Client ID
You can obtain a Client ID by visting the Soundcloud website and inspecting network traffic (perhaps with Chrome DevTools or some HTTP proxy software) and looking for any requests to the Soundcloud API. Ex:
```
https://api-v2.soundcloud.com/me/play-history/tracks?client_id={CLIENT ID IS HERE}&limit=25&offset=0&linked_partitioning=1&app_version=1590494738&app_locale=en
```
