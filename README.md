# replayOBS
Das folgende Prinzip (siehe Skizze) wurde von mir zuerst unter Windows 10 mit einer lokal angebundenen Webcam getestet.
So funktioniert es auch mit unseren IP-Kameras. Dazu hole ich mir mit FFmpeg den RTSP-Stream und splitte ihn in einen "UDP-Livestream" und eine "HLS Wiedergabelistendatei" auf. Ich möchte zwei HLS-Wiedergabelisten für den Abruf in OBS anlegen, einen "Short-Replay", der die letzten 5 Minuten und einen "Long-Replay", der den gesamten Kamerastream der Veranstaltung enthält.  
- [Hier gibt es die offizielle FFmpeg-Dokumentation](https://ffmpeg.org/ffmpeg-all.html#hls-2)  
- [und hier gibt es einen ausführlichen Blog zum Thema.](https://www.martin-riedl.de/2020/04/17/using-ffmpeg-as-a-hls-streaming-server-overview/)  
In unserem Gesamtkonzept gibt es folgende Streamweiterleitung:  
- In der RaspiBox wird mittels FFmpeg der RTSP-Stream von der IP-Kamera geholt
- und mittels SRT zur StreamBox gesendet.
- Auf der StreamBox wird mittels SRT-Live-Transmit oder FFmpeg der Stream entgegengenommen und in einen "Live-Stream" und die "Short- und Long-Replay"-Dateien aufgesplittet.  
![Prinzipskizze](https://github.com/snowgames95/replayOBS/blob/a4048cd217097d43c54f30e19b4fd4955dc5cec4/FFmpeg_OBS_ReplayHLS.png)
