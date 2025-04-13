## Video to GIF Conversion

Convert video to GIF with default settings:
```
ffmpeg -i video.mkv -vf "fps=10,scale=720:-1:flags=lanczos" -loop 0 output.gif
```

Create a smaller GIF:
```
ffmpeg -i video.mkv -vf "fps=10,scale=120:-1:flags=lanczos" -loop 0 output.gif
```

Extract a specific section of a video (from 3 to 8 seconds) and convert to GIF:
```
ffmpeg -ss 3 -to 8 -i video.mkv -vf "fps=10,scale=1280:-1:flags=lanczos" -loop 0 output.gif
```



## Feature Phone Video Conversion

### For Nokia 230 and similar feature phones

Convert videos with various bitrate options:

64 kbps audio, 256 kbps video:
```
ffmpeg -i input_video.mp4 -vf "scale=iw*min(240/iw\,320/ih):ih*min(240/iw\,320/ih),setsar=1" -c:v mpeg4 -b:v 256k -c:a aac -b:a 64k output_video.mp4
```

64 kbps audio, 320 kbps video:
```
ffmpeg -i input_video.mp4 -vf "scale=iw*min(240/iw\,320/ih):ih*min(240/iw\,320/ih),setsar=1" -c:v mpeg4 -b:v 320k -c:a aac -b:a 64k output_video.mp4
```

64 kbps audio, 512 kbps video:
```
ffmpeg -i input_video.mp4 -vf "scale=iw*min(240/iw\,320/ih):ih*min(240/iw\,320/ih),setsar=1" -c:v mpeg4 -b:v 512k -c:a aac -b:a 64k output_video.mp4
```

64 kbps audio, 768 kbps video:
```
ffmpeg -i input_video.mp4 -vf "scale=iw*min(240/iw\,320/ih):ih*min(240/iw\,320/ih),setsar=1" -c:v mpeg4 -b:v 768k -c:a aac -b:a 64k output_video.mp4
```

128 kbps audio, 768 kbps video:
```
ffmpeg -i input_video.mp4 -vf "scale=iw*min(240/iw\,320/ih):ih*min(240/iw\,320/ih),setsar=1" -c:v mpeg4 -b:v 768k -c:a aac -b:a 128k output_video.mp4
```


## These commands assume you have opened the terminal in the video directory.




# Bach convert from the same folder all wav file to mp3 and same in a folder name converted
```bash
mkdir -p converted
for f in *.wav; do
  ffmpeg -i "$f" -q:a 0 "converted/${f%.wav}.mp3"
done
```


## start from 5 second
```bash
ffmpeg -ss 5 -i input.mp3 -acodec copy output.mp3
```
```bash
ffmpeg -ss 5 -i input.mp3 -vn -acodec libmp3lame -b:a 192k output.mp3
```
