Web4Radio
==========

Web4Radio is a web-based player for Icecast and SHOUTcast streams that works in almost any browser, including those in mobile devices. It uses [jPlayer](http://jplayer.org/) to provide playback via Adobe Flash and HTML5 technologies. The goal is to allow broadcasters to reach as many listeners across platforms and devices as possible, without much technical effort.   


Demo
--------

You can launch a player at my station, [Radio Thermo](http://radiothermo.com/)

*Note*: My station occasionally plays tracks that some may find offensive; listener discretion is advised. If the current track says "Offline", the player isn't broken, I forgot to program content! The station provides MP3 and OGG streams via an Icecast-kh server.      

Compatibility
-----------------

Web4Radio supports the following server types:

- Icecast2
- Icecast-kh
- SHOUTcast

*Note*: SHOUTcast2 is not supported at this time. If you operate a SHOUTcast2 server, have an in-depth knowledge of its configuration, and would like to help with testing, please [reply to the issue in the tracker](https://github.com/seanthegeek/Web4Radio/issues/3).

The following codecs are currently supported:

- MP3
- OGG Vorbis

*Note*: AAC support will be added in a [future release](https://github.com/seanthegeek/Web4Radio/issues/1). Due to limitations in Adobe Flash Player and browsers, AAC+ streams are unlikely to be supported in the future

To provide maximum compatibility, you should provide both an MP3 stream and and OGG stream. However, if you can only supply one format, it should be MP3. Most browsers support MP3; OGG provides a nice fallback for the rare case that a browser that does not support MP3 (e.g. non-mobile Firefox), and does not have Flash installed. IE and Safari do not support OGG out-of-the box.

Web4Radio has been successfully tested in the following browsers:

- Internet Explorer
- Mozilla Firefox
- Google Chrome
- Apple Safari
- Opera

- Mobile Safari (iPhone, iPad, Apple iOS 6)
- Android >= 4.1 stock browser (users of older versions will be prompted to use [Firefox for Android](https://play.google.com/store/apps/details?id=org.mozilla.firefox))
- Windows Phone 8

The player probably works with most other modern devices/browsers. If you have successfully tested a browser/device that is not listed here, please open an issue in the tracker for it to be added.

 Setup
----------

The dependent components for Web4Radio are hosted by the free [jsDelivr](http://www.jsdelivr.com/) [CDN](https://en.wikipedia.org/wiki/Content_delivery_network). The only file that needs to be uploaded to your web server is a modified copy of the `player.html` file. The CDN is used for for those who cannot upload their own non-HTML content. If you do not trust the CDN, you should host the dependencies yourself, and modify the player code accordingly.

1. Download a copy of this repository as a zip using the download button at the top of the Web4Radio repository page.
2. Extract player.html from the zip
3. Set the player options (within the quote marks), located at the bottom of the head section:

 - `streamName` - The written name of your stream
 - `streamAddress` - The server's address
 - `streamPort` - The server's [port number](https://en.wikipedia.org/wiki/Uniform_resource_locator#Syntax)
 - `mp3Mount` - The name of the Iceast MP3 mount, without `/`s. If not applicable, (e.g. for SHOUTcast streams), leave as empty quotes `""`
 - `oggMount` - The name of the Iceast OGG mount, without `/`s. If not applicable, (e.g. for SHOUTcast streams), leave as empty quotes `""`
 - `autoPlay` - Sets automatic playback
 - `stationId` - If you are a [StreamLicensing.com](http://streamlicensing.com/) customer, enter your station ID number here to display the currently playing track in the player; all others should leave this set to empty quotes. [Later versions](https://github.com/seanthegeek/Web4Radio/issues/3) of the player will provide now playing metadata for all users. To locate your station ID, log into the  [StreamLicensing.com client area](http://streamlicensing.com/), and edit your station, the URL in the address bar will then contain `id=` where the following number is the station ID.

4. Save the modified player.html file, and upload it to your web server. The player code must be in a separate file/page, even if you plan to embed it in an existing page.

5. The player can then be launched in a popup from a link like this:

```<a onclick="window.open('http://www.streamlicensing.com/stations/radiothermo/player.html', 'player', 'menubar=no,location=yes,resizable=yes,scrollbars=no,status=no, width=300, height=200');">Launch radio player</a>```

Or, it can be embedded in an existing page as an `iframe` like this one:

```<iframe src=http://www.streamlicensing.com/stations/radiothermo/player.html" width="300" height="300" scrolling="no" frameborder="0">```

When using an embedded player, consider turning off auto play. Unsolicited sound may annoy visitors.  

Replace the URLs in the above examples so that it points the page you uploaded on your site. It is best to use absolute URLs; some versions of IE don't like relative URLs.

The height may need to be adjusted if you do not show the song information, or need to show longer song information.

Known issues
-------------------

The issues below are caused by bugs in various browsers. Web4Radio does its best to avoid and/or work around them, but they can still cause problems in certain circumstances. **Please do not report issues for known issues**. If you have a working fix, please submit a pull request.  

- Android browsers do not automatically play
- Android users on a slow/failed connection are sometimes shown the "incompatable browser" message as a false-positive
- [Broken playback does not resume properly on non-mobile browsers without Flash](https://github.com/happyworm/jPlayer/issues/165)
- [When only an OGG stream with metadata is supplied (so MP3 can't be used instead), playback stops after each track in Google Chrome](https://github.com/happyworm/jPlayer/issues/160)

FAQ
-------

- How can I customize the player's apperence?

 Override the CSS of the jPlayer [Blue Monday](http://jplayer.org/latest/jPlayer.Blue.Monday.2.4.0.zip) skin. 

- I tried to get jPlayer working with SHOUTcast, but couldn't. What did you do differently?

 When using a browser to access a SHOUTcast stream, you must append a `;` to the end of the stream URL, otherwise SHOUTcast will serve the status page, rather than the stream. Web4Radio does this automatically for the user.

 Source: [Stack Overflow](http://stackoverflow.com/questions/1273454/how-to-stream-a-shoutcast-radio-broadcast-in-flash-shoutcast-flash-player)

- Where are the volume controls?

 On mobile devices, the volume is controlled via the device's phyisical controls. 

Support
----------

If you encounter a problem with Web4Radio, please use the [issue tracker](https://github.com/seanthegeek/Web4Radio/issues).

Donations
--------------

If Web4Radio has helped you increase your revenue, please consider [donating to the jPlayer project](http://jplayer.org). Without the hard work of the jPlayer team, Web4Radio would not exist.
