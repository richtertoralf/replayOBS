# replayOBS

![Status](https://img.shields.io/badge/Status-Denkansatz-blue)
![Stack](https://img.shields.io/badge/Stack-FFmpeg%20%2B%20OBS-green)
![Budget](https://img.shields.io/badge/Budget-Low--Budget-orange)

Ein sehr einfacher Replay-Ansatz für OBS mit FFmpeg.

>**Früher Denkansatz für ein sehr einfaches Replay.**
>Mich interessierte nicht, wie man mit großem Broadcast-Budget arbeitet, sondern wie man mit einfachsten Mitteln einen großen Teil des praktischen Nutzens trotzdem erreicht.
>Dass solche Low-Budget-Ansätze im etablierten Produktionsumfeld nicht immer freundlich aufgenommen wurden, gehört zur Geschichte dahinter.

**Kein professionelles Replay-System, sondern ein schneller technischer Workaround:
Live nach OBS, parallel Segmente schreiben, daraus grobes Replay abspielen.**

Gedacht für kleine Setups und als Anregung für Leute, die mit FFmpeg und OBS arbeiten.

>Für grobe Rückblicke ist das vermutlich einer der simpelsten praktikablen Ansätze überhaupt, wenn man nur mit FFmpeg, Dateien/Segmenten und OBS arbeiten will.

FFmpeg holt den RTSP-Stream der Kamera und erzeugt parallel:

- Live für OBS
- HLS für Replay

Gedacht für Short-Replay der letzten 5 Minuten und ein Long-Replay der gesamten Veranstaltung.

Ablauf:

- RaspiBox: RTSP → SRT
- StreamBox: SRT → Live + Replay

Das folgende Prinzip (siehe Skizze) habe ich 2021 unter Windows 10 mit einer lokal angebundenen Webcam getestet.
So funktioniert es auch mit unseren IP-Kameras. Dazu hole ich mir mit FFmpeg den RTSP-Stream und splitte ihn in einen "UDP-Livestream" und eine "HLS Wiedergabelistendatei" auf. Ich möchte zwei HLS-Wiedergabelisten für den Abruf in OBS anlegen, einen "Short-Replay", der die letzten 5 Minuten und einen "Long-Replay", der den gesamten Kamerastream der Veranstaltung enthält.  
- [Hier gibt es in der offiziellen FFmpeg-Dokumentation Infos zur Erzeugung der HLS-Wiedergabedateien](https://ffmpeg.org/ffmpeg-all.html#hls-2)  
- [und hier gibt es einen ausführlichen Blog zum Thema.](https://www.martin-riedl.de/2020/04/17/using-ffmpeg-as-a-hls-streaming-server-overview/)  

In unserem Gesamtkonzept gibt es folgende Streamweiterleitung:  
- In der RaspiBox wird mittels FFmpeg der RTSP-Stream von der IP-Kamera geholt
- und mittels SRT zur StreamBox gesendet.
- Auf der StreamBox wird mittels SRT-Live-Transmit oder FFmpeg der Stream entgegengenommen und in einen "Live-Stream" und die "Short- und Long-Replay"-Dateien aufgesplittet.  

![Prinzipskizze](https://github.com/snowgames95/replayOBS/blob/a4048cd217097d43c54f30e19b4fd4955dc5cec4/FFmpeg_OBS_ReplayHLS.png)
