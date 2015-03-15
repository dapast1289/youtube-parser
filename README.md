# youtube-parser
A tool to extract URLs and format info from YouTube page.
This is almost based on the node-ytdl-core by @fent, just attempting to make it work in browser as well.

##CLI

```
Usage:
  $ youtube-parser url [options]

Examples:
  $ youtube-parser https://www.youtube.com/watch?v=C_vqnySNhQ0 --container mp4
  $ youtube-parser https://youtu.be/C_vqnySNhQ0 --quality medium

Options:
  -h, --help           Print help
  -v, --version        Print version
  -q, --quality        List all URLs of video with the specified quality {small | medium | large}
  -c, --container      List all URLs of video with the specified container format {mp4 | webm | flv | 3gp}
  -e, --encoding       List all URLs of video with the specified video encoding {VP8 | H.264 | Sorenson H.283 | MPEG-4 Visual}
  -a, --audioEncoding  List all URLs of video with the specified audio encoding {mp3 | aac | vorbis}
  --videoOnly          List all URLs of video that consists of only a video track
  --audioOnly          List all URLs of video that consists of only an audio track
```

##API

### getMetadata
```
Promise getMetadata(string url)
```

* url - 'watch video' page on YouTube.
* return value - A promise object to resolve with an object containing actual URLs and format info of the page's video.

### getURL
```
Promise getMetadata(string url, object format)
```

* url - 'watch video' page on YouTube.
* format - Desired format of the video.
* return value - A promise object to resolve with an array of URL/format info objects that matche the requested format.

###Example
```js
var youTubeParser = require('youtube-parser');

youTubeParser.getMetadata('https://www.youtube.com/watch?v=C_vqnySNhQ0')
.then(
  function (metadata) {
    // Access video info.
  }
);

youTubeParser.getURL('https://youtu.be/C_vqnySNhQ0', {quality: 'medium', container: 'mp4'})
.then(
  function (urlList) {
    console.log(urlList[0]);
  }
);
```
