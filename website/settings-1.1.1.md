Liquidsoap configuration
========================
ALSA configuration
------------------
### Alsa internal buffer size
Default: `0`

```
set("alsa.alsa_buffer",0)
```

This setting is only used in buffered alsa I/O, and affects latency.
Set to 0 to disable this setting and use ALSA's default.

### Buffer size, in frames
Default: `1`

```
set("alsa.buffer_length",1)
```

This is only used for buffered ALSA I/O, and affects latency.

### Number of periods
Default: `0`

```
set("alsa.periods",0)
```

Set to 0 to disable this setting and use ALSA's default.

Audio settings
--------------
### Conversion settings
#### Samplerate conversion settings
##### Libsamplerate conversion settings
###### Resampling quality
Default: `"fast"`

```
set("audio.converter.samplerate.libsamplerate.quality","fast")
```

Resampling quality, one of: ``best'', ``medium'', ``fast'', ``zero_order'', ``linear''. Refer to ocaml-samplerate for details.

##### Preferred samplerate converter
Default: `"libsamplerate"`

```
set("audio.converter.samplerate.preferred","libsamplerate")
```

Preferred samplerate converter.

Audioscrobbler configuration.
-----------------------------
Clock settings
--------------
### Handling of streaming errors
Default: `false`

```
set("clock.allow_streaming_errors",false)
```

Control the behaviour of clocks when an error occurs during streaming.
This has no effect on errors occurring during source initializations.
By default, any error will cause liquidsoap to shutdown. If errors
are allowed, faulty sources are simply removed and clocks keep running.
Allowing errors can result in complex surprising situations;
use at your own risk!

Decoder settings
----------------
### Maximum debugging information (dev only)
Default: `false`

```
set("decoder.debug",false)
```

WARNING: Do not enable unless a developer instructed you to do so!
The debugging mode makes it easier to understand why decoding fails,
but as a side effect it will crash liquidsoap at the end of every
track.

### Decoders and order used to decode files.
Default: ```
["META","WAV","MIDI","IMAGE","FLAC","AAC","MP4","OGG","MAD","GSTREAMER"]```


```
set("decoder.file_decoders",["META","WAV","MIDI","IMAGE","FLAC","AAC","MP4","OGG","MAD","GSTREAMER"])
```

### File extensions used for guessing audio formats
#### File extensions used for guessing AAC format
Default: `["aac"]`

```
set("decoder.file_extensions.aac",["aac"])
```

#### File extensions used for guessing FLAC format
Default: `["flac"]`

```
set("decoder.file_extensions.flac",["flac"])
```

#### File extensions used for guessing format handled by GStreamer
Default: `["wmv","avi","mp4","3gp","webm","mkv"]`

```
set("decoder.file_extensions.gstreamer",["wmv","avi","mp4","3gp","webm","mkv"])
```

#### File extensions used for guessing mpeg audio format
Default: `["mp3","mp2","mp1"]`

```
set("decoder.file_extensions.mad",["mp3","mp2","mp1"])
```

#### File extensions used for guessing MP3 format (DEPRECATED, use *.mad configuration keys!)
Default: `["mp3","mp2","mp1"]`

```
set("decoder.file_extensions.mp3",["mp3","mp2","mp1"])
```

#### File extensions used for guessing MP4 format
Default: ```
["m4a","m4b","m4p","m4v","m4r","3gp","mp4"]```


```
set("decoder.file_extensions.mp4",["m4a","m4b","m4p","m4v","m4r","3gp","mp4"])
```

#### File extensions used for guessing OGG format
Default: `["ogv","oga","ogx","ogg","opus"]`

```
set("decoder.file_extensions.ogg",["ogv","oga","ogx","ogg","opus"])
```

#### File extensions used for decoding metadata using TAGLIB
Default: `["mp3"]`

```
set("decoder.file_extensions.taglib",["mp3"])
```

#### File extensions used for guessing WAV format
Default: `["wav"]`

```
set("decoder.file_extensions.wav",["wav"])
```

### Decoders and order used to decode image files.
Default: `["PPM","CAMLIMAGES","SDL/IMAGE"]`

```
set("decoder.image_file_decoders",["PPM","CAMLIMAGES","SDL/IMAGE"])
```

### Mime-types used for guessing audio formats
#### Mime-types used for guessing AAC format
Default: ```
["audio/aac","audio/aacp","audio/x-hx-aac-adts"]```


```
set("decoder.mime_types.aac",["audio/aac","audio/aacp","audio/x-hx-aac-adts"])
```

#### Mime-types used for guessing PCM/BASIC format
Default: `["audio/basic"]`

```
set("decoder.mime_types.basic",["audio/basic"])
```

#### Mime-types used for guessing FLAC format
Default: `["audio/x-flac"]`

```
set("decoder.mime_types.flac",["audio/x-flac"])
```

#### Mime-types used for guessing format handled by GStreamer
Default: ```
["video/x-ms-asf","video/x-msvideo","video/mp4","video/3gpp","video/webm","video/x-matroska","video/mp2t","video/MP2T"]```


```
set("decoder.mime_types.gstreamer",["video/x-ms-asf","video/x-msvideo","video/mp4","video/3gpp","video/webm","video/x-matroska","video/mp2t","video/MP2T"])
```

#### Mime-types used for guessing mpeg audio format
Default: `["audio/mpeg","audio/MPA"]`

```
set("decoder.mime_types.mad",["audio/mpeg","audio/MPA"])
```

#### Mime-types used for guessing MP3 format (DEPRECATED, use *.mad configuration keys!)
Default: `["audio/mpeg","audio/MPA"]`

```
set("decoder.mime_types.mp3",["audio/mpeg","audio/MPA"])
```

#### Mime-types used for guessing MP4 format
Default: `["audio/mp4","application/mp4"]`

```
set("decoder.mime_types.mp4",["audio/mp4","application/mp4"])
```

#### Mime-types used for guessing OGG format.
Default: ```
["application/ogg","application/x-ogg","audio/x-ogg","audio/ogg","video/ogg"]```


```
set("decoder.mime_types.ogg",["application/ogg","application/x-ogg","audio/x-ogg","audio/ogg","video/ogg"])
```

#### Mime-types used for decoding metadata using TAGLIB
Default: `["audio/mpeg"]`

```
set("decoder.mime_types.taglib",["audio/mpeg"])
```

#### Mime-types used for guessing WAV format
Default: ```
["audio/vnd.wave","audio/wav","audio/wave","audio/x-wav"]```


```
set("decoder.mime_types.wav",["audio/vnd.wave","audio/wav","audio/wave","audio/x-wav"])
```

### Decoders and order used to decode streams.
Default: ```
["WAV","PCM/BASIC","FLAC","AAC","OGG","MAD","GSTREAMER"]```


```
set("decoder.stream_decoders",["WAV","PCM/BASIC","FLAC","AAC","OGG","MAD","GSTREAMER"])
```

### Taglib settings
#### By default, taglib will only attempt reading metadata from files that it detects as valid. This may fail, for example if the reported mime type isn't ``audio/mpeg''. If you set this configuration key to true, then all files successfully recognized by liquidsoap will be considered as MPEG by taglib. In this case, taglib configuration keys for file extensions and mime types (``decoder.file_extensions.taglib'' and ``decoder.mime_types.taglib'') are not used, and file detection is only done based on the corresponding settings from the MAD MPEG decoder.
Default: `false`

```
set("decoder.taglib.force_mpeg",false)
```

Encoder settings
----------------
### Metadata settings
#### Exported metdata
Default: ```
["artist","title","album","genre","date","tracknumber","comment","track","year"]```


```
set("encoder.encoder.export",["artist","title","album","genre","date","tracknumber","comment","track","year"])
```

The list of labels of exported metadata.

Frame format
------------
### Audio (PCM) format
#### Default number of channels
Default: `2`

```
set("frame.audio.channels",2)
```

#### Samplerate
Default: `44100`

```
set("frame.audio.samplerate",44100)
```

### Tentative frame duration in seconds
Default: `0.04`

```
set("frame.duration",0.04)
```

Audio and video samplerates constrain the possible frame durations.
This setting is used as a hint for the duration, when 'frame.audio.size'
is not provided.
Tweaking frame duration is tricky but needed when dealing with latency
or getting soundcard I/O correctly synchronized with liquidsoap.

### MIDI parameters
#### Default number of channels
Default: `0`

```
set("frame.midi.channels",0)
```

### Video format
#### Default number of channels
Default: `0`

```
set("frame.video.channels",0)
```

#### Image height
Default: `240`

```
set("frame.video.height",240)
```

#### Samplerate
Default: `25`

```
set("frame.video.samplerate",25)
```

#### Image width
Default: `320`

```
set("frame.video.width",320)
```

Media decoding/endcoding through gstreamer.
-------------------------------------------
### Add borders in order to keep video aspect ratio.
Default: `true`

```
set("gstreamer.add_borders",true)
```

### Debug level (bewteen 0 and 5).
Default: `0`

```
set("gstreamer.debug_level",0)
```

### Maximal number of buffers.
Default: `10`

```
set("gstreamer.max_buffers",10)
```

Harbor settings (Icecast/shoutcast stream receiver).
----------------------------------------------------
### IP address on which the harbor should listen.
Default: `"0.0.0.0"`

```
set("harbor.bind_addr","0.0.0.0")
```

### Content-type (mime) of formats which allow shout metadata update.
Default: ```
["audio/mpeg","audio/aacp","audio/aac","audio/x-aac","audio/wav","audio/wave","audio/x-flac"]```


```
set("harbor.icy_formats",["audio/mpeg","audio/aacp","audio/aac","audio/x-aac","audio/wav","audio/wave","audio/x-flac"])
```

### Maximun of pending source requests per port.
Default: `2`

```
set("harbor.max_connections",2)
```

### Perform reverse DNS lookup to get the client's hostname from its IP.
Default: `true`

```
set("harbor.reverse_dns",true)
```

### Timeout for network operations.
Default: `300.`

```
set("harbor.timeout",300.)
```

### Display passwords, for debugging.
Default: `false`

```
set("harbor.verbose",false)
```

initialization configuration
----------------------------
### catch exceptions, use false to backtrace exceptions
Default: `true`

```
set("init.catch_exn",true)
```

### run initialization using concurrent threads
Default: `false`

```
set("init.concurrent",false)
```

### run in daemon mode
Default: `false`

```
set("init.daemon",false)
```

#### Changes the effective user (drops privileges).
Default: `false`

```
set("init.daemon.change_user",false)
```

##### Group used to run the daemon.
Default: `"daemon"`

```
set("init.daemon.change_user.group","daemon")
```

##### User used to run the daemon.
Default: `"daemon"`

```
set("init.daemon.change_user.user","daemon")
```

#### support for pidfile generation
Default: `true`

```
set("init.daemon.pidfile",true)
```

##### path to pidfile
Default: `"<sysrundir>/<script>.pid"`

```
set("init.daemon.pidfile.path","<sysrundir>/<script>.pid")
```

### Start liquidsoap even without any active source
Default: `false`

```
set("init.force_start",false)
```

This should be reserved for advanced dynamic uses of liquidsoap.

### dump an initialization trace
Default: `false`

```
set("init.trace",false)
```

log configuration
-----------------
### log to file
Default: `true`

```
set("log.file",true)
```

#### append log to the file
Default: `true`

```
set("log.file.append",true)
```

#### path to log file
Default: `"<syslogdir>/<script>.log"`

```
set("log.file.path","<syslogdir>/<script>.log")
```

#### log file permissions
Default: `384`

```
set("log.file.perms",384)
```

### general log level
Default: `3`

```
set("log.level",3)
```

### log to stdout
Default: `false`

```
set("log.stdout",false)
```

### Enable syslog logging.
Default: `false`

```
set("log.syslog",false)
```

#### Logging facility.
Default: `"DAEMON"`

```
set("log.syslog.facility","DAEMON")
```

#### Name of the program.
Default: `"liquidsoap"`

```
set("log.syslog.program","liquidsoap")
```

### display unix timestamps (subsecond accuracy, timezone independant)
Default: `false`

```
set("log.unix_timestamps",false)
```

Parameters for the mpd protocol.
--------------------------------
### MPD host.
Default: `"127.0.0.1"`

```
set("mpd.host","127.0.0.1")
```

### Directory where MPD's music is located.
Default: `"/var/lib/mpd/music"`

```
set("mpd.path","/var/lib/mpd/music")
```

### MPD port.
Default: `6600`

```
set("mpd.port",6600)
```

### Randomize order of MPD's results.
Default: `true`

```
set("mpd.randomize",true)
```

Interactions through the OSC protocol.
--------------------------------------
### Port for OSC server.
Default: `7777`

```
set("osc.port",7777)
```

Playlist formats
----------------
### Cue in metadata for playlists with track index.
Default: `"liq_cue_in"`

```
set("playlists.cue_in_metadata","liq_cue_in")
```

Some playlists format, such as CUE files specify index points to start
tracks playback. In this case, tracks are resolved to a annotate: request with
a cue-in metadata containing the index. If you want to make use of this index,
you should specify here what label you want for this metadata and use the cue_cut
operator on the resulting source

### Cue out metadata for playlists with track index.
Default: `"liq_cue_out"`

```
set("playlists.cue_out_metadata","liq_cue_out")
```

Some playlists format, such as CUE files specify index points to start
tracks playback. In this case, tracks are resolved to a annotate: request with
a cue-in metadata containing the index. If you want to make use of this index,
you should specify here what label you want for this metadata and use the cue_cut
operator on the resulting source

### Mime-types used for guessing playlist formats.
#### Mime types associated to XML-based playlist formats
Default: ```
["video/x-ms-asf","audio/x-ms-asx","text/xml","application/xml","application/smil","application/smil+xml","application/xspf+xml","application/rss+xml"]```


```
set("playlists.mime_types.xml",["video/x-ms-asf","audio/x-ms-asx","text/xml","application/xml","application/smil","application/smil+xml","application/xspf+xml","application/rss+xml"])
```

requests configuration
----------------------
### Time (in seconds) after which a destroyed request cannot be accessed anymore.
Default: `600.`

```
set("request.grace_time",600.)
```

### Decoders and order used to decode files' metadata.
Default: ```
["FLAC","MP4","OGG","TAGLIB","GSTREAMER"]```


```
set("request.metadata_decoders",["FLAC","MP4","OGG","TAGLIB","GSTREAMER"])
```

#### Compute duration in the ``duration'' metadata, if the metadata is not already present. This can take a long time and the use of this option is not recommended: the proper way is to have a script precompute the ``duration'' metadata.
Default: `false`

```
set("request.metadata_decoders.duration",false)
```

#### Allow metadata resolvers to override metadata already set through annotate: or playlist resolution for instance.
Default: `false`

```
set("request.metadata_decoders.override",false)
```

Streaming clock settings
------------------------
### Maximum latency in seconds
Default: `60.`

```
set("root.max_latency",60.)
```

If the latency gets higher than this value, the outputs will be reset,
instead of trying to catch it up second by second.
The reset is typically only useful to reconnect icecast mounts.

Parameters for the say protocol.
--------------------------------
### Program for syntesizing voices (takes as argument the text, the file to synthesize to, and optionnaly the voice to use).
Default: ```
"/usr/local/lib/liquidsoap/1.1.1/liquidtts"```


```
set("say.program","/usr/local/lib/liquidsoap/1.1.1/liquidtts")
```

Internal scheduler
------------------
### Fast queues
Default: `0`

```
set("scheduler.fast_queues",0)
```

Number of queues that are dedicated to fast tasks.
It might be useful to create some if your request resolutions,
or some user defined tasks (cf. `add_timeout()`), are
delayed too much because of slow tasks blocking the generic queues,
such as last.fm submissions or slow `add_timeout` handlers.

### Generic queues
Default: `2`

```
set("scheduler.generic_queues",2)
```

Number of event queues accepting any kind of task.
There should at least be one. Having more can be useful to avoid that
trivial request resolutions (local files) are not delayed because of
a stalled download. But N stalled download can block N queues anyway.

### Log scheduler messages
Default: `false`

```
set("scheduler.log",false)
```

### Non-blocking queues
Default: `2`

```
set("scheduler.non_blocking_queues",2)
```

Number of queues dedicated to internal non-blocking tasks.
These are only started if such tasks are needed.
There should be at least one.

Server configuration
--------------------
### Support for communication via a UNIX domain socket interface
Default: `false`

```
set("server.socket",false)
```

The main advantage of this method is that you can set very precisely
the access permissions for the socket, just like for any other file.
A useful command to use this interface is: ``socat stdin unix:<path>''.

#### Path of the UNIX domain socket
Default: `"<sysrundir>/<script>.sock"`

```
set("server.socket.path","<sysrundir>/<script>.sock")
```

In this filename, <pid>, <script> and <sysrundir> are replaced by 
their respective values: PID of the instance of liquidsoap,
base name of the .liq script (if any), default runtime data directory.

#### Socket permissions, up to umask
Default: `384`

```
set("server.socket.permissions",384)
```

This parameter is better written in octal notation. Although you can 
write octal numbers like 0o660, they are not displayed back in octal. 
For example, the default value 384 is the decimal for 0o600.

### Support for communication via a telnet interface
Default: `false`

```
set("server.telnet",false)
```

This allows you to communicate with the server via a telnet interface,
i.e., a simple text-based communication over TCP.
The standard ``telnet'' command will allow you to communicate through
that interface, as well as the telnet libraries available in most
script languages.
Since there is currently no authentication, you should be careful
about who can access this interface: either restrict it to connections
from localhost (using the bind_addr param) or set up a firewall.

#### Network mask from which the telnet server should accept connections
Default: `"127.0.0.1"`

```
set("server.telnet.bind_addr","127.0.0.1")
```

#### Port on which the telnet server should listen
Default: `1234`

```
set("server.telnet.port",1234)
```

#### Perform reverse DNS lookup to get the client's hostname from its IP.
Default: `true`

```
set("server.telnet.reverse_dns",true)
```

### Timeout for read/write operations.
Default: `30.`

```
set("server.timeout",30.)
```

A negative value disables timeout.

Settings related to metadata tags
---------------------------------
### List of encodings to try for automatic encoding detection
Default: `["UTF-8","ISO-8859-1"]`

```
set("tag.encodings",["UTF-8","ISO-8859-1"])
```

Video settings
--------------
### Video conversion
#### Gavl converter
##### Conversion quality
Default: `2`

```
set("video.converter.gavl.quality",2)
```

Quality setting for gavl video conversion. Range from 1 to 5

##### Scale mode
Default: `"auto"`

```
set("video.converter.gavl.scale_mode","auto")
```

Scale mode. Values must be one of: 
``auto''
``nearest''
``bilinear''
``quadratic''
``cubic_bspline''
``cubic_mitchell''
``cubic_catmull''
``scale_sinc_lanczos''

#### Preferred video converter
Default: `"gavl"`

```
set("video.converter.preferred","gavl")
```

#### Preferred proportional scale.
Default: `true`

```
set("video.converter.proportional_scale",true)
```


