# Streaming info
Since I don't want to dedicate a portable device to running this for the next 3+ weeks, I've decided to use a Windows Server 2016 VM on my ESXi homelab. Of course your setup will vary, but the important thing is to have a device that can reliably source the camera stream, do any OBS magic you need, and subsequently push it to Youtube (or whatever service).

## Open Broadcast System (OBS)
### Version
Since I'm using Windows Server 2016, apparently the newest [OBS I can use is v28](https://github.com/obsproject/obs-studio/releases/tag/28.1.2) (which is weird since Server 2016 is the Win 10 codebase, and the latest OBS does do 10 still? IDK, the path of least resistance is to just use v28 which seems to work just fine).

### Recording
Since I love making timelapses, and might want to review if we miss some exiting hatching stuff, I'm also using OBS to record. Since we've got 20.5 days to go, and trying to save that all into one video container (file) sounds like asking for trouble, in OBS's settings on the `Output` page I switched to the Advanced view and enabled `Automatic File Splitting` by file size of `2048 MB`. 

### Sources
#### Wyze Cam v3
Although I have had some luck with the RSTP firmware, the camera I'm using had the wz_hacks_mini on it at one point (and I intended to use this as well but it wasn't booting -- could be that the ~20y/o 8GB uSD card I'm using finally bit the dust!), so instead similar to my WS2016 situation I'm just using Docker Wyze Bridge (which I'm already running in my HomeAssistant for a v3pro cam) to restream into RTSP. OBS accepts this fine by adding a `Media Source`, unchecking the `Local File` and `Restart playback when source becomes active` options, and dropping the RTSP URL right from the bridge in the input box.
#### Browser
I haven't added it yet, but this is how I plan to add the metadata to the stream.

## Youtube setup
Seems like you need to do some extra verification to be able to live stream; in my case I just had to hand over my phone number... pretty sure AlphabetCorp already had that 😅. Weirdly although it's not mentioned, I got errors trying to stream inside OBS until I went into the "[Youtube Studio](https://studio.youtube.com)" for the first time, which then presented with me a message to this effect:
>### Only 23:53:46 until you can stream  
>You requested streaming access on May 1, 2024 at 2:02 PM. Once it’s available on your channel, you can schedule streams or go live instantly.
