# Live Audio Player

Made to be a OBS Browser Source. Connects to a websocket server of your choice for you to control with whatever you like. Simple websocket api with events, see more below.

Not for beginners!

## Setup

Websocket Server:  
Set the full websocket url in line 13 inside the player.html

Audio Files:
wav or mp3 work best. ogg should also work. Place the sound files in the same directory as the player.html  
Add or remove entrys to the array of json objects starting line 10 inside the player.html to configure the files that you want available.  
Just make sure you use unique names for the files.

## WS API Docs:

`file` = filename without filextension
`volValue` = 0-1, float
`timeInSec` = time left in playback, in sec(thanks chromium) (updates multiple times a sec)

Requests: (websocket server -> player.html)  
Play file: `{"dst": "file", "action": "play"}`  
Pause playback: `{"dst": "file", "action": "pause"}`  
Stop playback: `{"dst": "file", "action": "stop"}`  
Set playback volume: `{"dst": "file", "action": "setVolume", "volume": volValue}`  

Events: (player.html -> websocket server)  
Time remaining: `{"update": "timeupdate","timeleft": timeInSec,"source": "file"}`  
Paused: `{"update": "pause","timeleft": timeInSec,"source": "file"}`  
Playing: `{"update": "playing","timeleft": timeInSec,"source": "file"}`  
Ended: `{"update": "ended","timeleft": timeInSec,"source": "file"}`  