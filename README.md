Test vids and test sounds.
Using references:
http://stackoverflow.com/questions/11779490/how-to-add-a-new-audio-not-mixing-into-a-video-using-ffmpeg
http://www.bogotobogo.com/FFMpeg/ffmpeg_video_test_patterns_src.php

Give a few test vids using ffmpeg.
Test bars with countdown:
./ffmpeg -f lavfi -i testsrc=duration=6:size=1280x720:rate=30 testsrc.mpg
Solid color:
./ffmpeg -f lavfi -i color=c=green:duration=6:s=1280x720:r=30 colorsrc.mpg

Add some audio:
./ffmpeg -i testsrc.mpg -i testpluck.mp3 -codec copy -shortest bars.mpg
./ffmpeg -i colorsrc.mpg -i testtone.mp3 -codec copy -shortest green.mpg

OK, so .mpg isn't allowed on the web.  Let's convert!
./ffmpeg -i bars.mpg bars.mp4
./ffmpeg -i green.mpg green.mp4