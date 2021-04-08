# replayOBS
Das folgende Prinzip wurde zuerst unter Windows 10 mit einer lokal angebundenen Webcam getestet.
So funktioniert es auch mit unseren IP-Kameras. Dazu hole ich mir mit FFmpeg den RTSP-Stream und splitte ihn in einen "UDP-Livestream" und eine "HLS Wiedergabelistendatei" auf. Ich möchte zwei HLS-Wiedergabelisten für den Abruf in OBS anlegen, einen "Short-Replay", der die letzten 5 Minuten und einen "Long-Replay", der den gesamten Kamerastream der Veranstaltung enthält.  
- [Hier gibt es die offizielle FFmpeg-Dokumentation](https://ffmpeg.org/ffmpeg-all.html#hls-2)  
- [und hier gibt es einen ausführlichen Blog zum Thema.](https://www.martin-riedl.de/2020/04/17/using-ffmpeg-as-a-hls-streaming-server-overview/)  
![Prinzipskizze](https://github.com/snowgames95/replayOBS/blob/a4048cd217097d43c54f30e19b4fd4955dc5cec4/FFmpeg_OBS_ReplayHLS.png)
