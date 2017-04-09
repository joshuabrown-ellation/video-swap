vidSwap

iOS devices can play a video audibly in the background when there's another video that
currently has focus.  My use case is serving ads via the ad tech Vendri.  I'll have my
show with focus in the foreground.  Then I'll pause my video in code to allow an ad to
play.  However, the ad plays inline, invisibly, behind the video that currently has
focus.  

For this test I create two videos and try different scenarios and see what breaks
what.  Honestly I don't know!

First test:
Two video tags on same level in dom, no css.  On hitting the external 'play' button 
in the markup, .play() method will be called on both videos simultaneously.  See
what happens when one video is in the markup before the other, and what happens when
you change the order in the code.

Since sound encoding that works on iphone is escaping me, I'll do this without it. 

Both videos will be a the same video, just one will have the audio go on and off
rapidly to indicate that it is playing.  Seriously, I really could not figure out
how to make an mp4 play on my iPhone!  Luckily I have an mp4 of Big Buck Bunny
that works on all my test devices.

Seriously?  Changing the video volume from javascript doesn't work on iOS by
default?  I really don't need this stress.  OK.  Must knuckle down and really
learn the H.264 codec for ffmpeg and do a test vid myself.