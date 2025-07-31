## install

```sh
wget "https://github.com/yt-dlp/yt-dlp/releases/download/2025.02.19/yt-dlp_linux" -O "./yt-dlp"

chmod +x "./yt-dlp"

sudo mv "./yt-dlp" "/usr/local/bin/yt-dlp"
```

## use

### audio

```sh
yt-dlp -f bestaudio --extract-audio --audio-format mp3 -o '%(title)s.%(ext)s' <url>

yt-dlp -f bestaudio --extract-audio --audio-format mp3 --audio-quality 320K --embed-thumbnail --add-metadata -o '%(title)s.%(ext)s' <url> 
```

### video

```sh
yt-dlp -S 'vcodec:h264,fps,res:720,acodec:m4a' -o '%(title)s.%(ext)s' <url>
```
