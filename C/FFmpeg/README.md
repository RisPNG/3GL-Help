# FFmpeg
This is sort of a separate thing as it has no ties with C, in a way, as it uses the [past standard for the C programming language, ISO C11](https://en.wikipedia.org/wiki/C11_\(C_standard_revision\)). [FFmpeg](https://ffmpeg.org/) is a media tool that allows user to do all sorts of operation including transcoding, file conversion, compression, etc.

## Installation
[Website](https://ffmpeg.org/).

## Demo and Usage
Once FFmpeg is installed, you can start performing operations through terminal.

### Video Conversion
```
ffmpeg -i input.mkv -c copy -map 0 output.mp4
```

This is the simplest way to convert any video format to another format. The examples shown above converts `*.mkv` (existing file in current folder) to `*.mp4`.

`-c` means codec. In a video, there are 3 types, `-c:a` selects audio, `-c:v` selects video, `-c:s` selects subtitle, and `-c` selects all of them. `-c copy -map 0` basically copies everything from the input and transcoded it into the output file, creating an identical video. `-i *.*` selects an input file. As for the output, FFmpeg just knows that the last argument in the command is the output file, so there's no such thing as `-o` or anything like it to identify output file.

### Video Compression
```
ffmpeg -i input.mkv -c:v libx264 -c:a copy -map 0 -crf 24 -preset veryfast output.mp4
```

### Video Downscaling
```
ffmpeg -i input.avi -filter:v scale=720:-1 -c:a copy output.mkv
```
```
ffmpeg -i input.avi -filter:v scale=720:-2 -c:a copy output.mkv
```

Whichever works.

### Audio Conversion to Mono
```
ffmpeg -i file.ext -ac 1 file_mono.ext
```

`*.ext` is any file format that has an audio stream.

### Video Trimming
```
ffmpeg -ss 00:01:00 -i input.mp4 -to 00:02:00 -c copy -map 0 output.mp4
```

Without re-encoding (faster):
```
ffmpeg -copyts -ss hh:mm:ss -i in.mp4 -to hh:mm:ss -c copy -map 0 out.mp4
```

### Video Conversion to Separate Frames
```
ffmpeg -i %1 -q:v 1 -qmin 1 -qmax 1 out-%1%%03d.jpg
```

This command converts every single frame exists in the video into separate .jpeg files in the same folder.
