Test vids and test sounds.
Using references:
http://stackoverflow.com/questions/11779490/how-to-add-a-new-audio-not-mixing-into-a-video-using-ffmpeg
http://www.bogotobogo.com/FFMpeg/ffmpeg_video_test_patterns_src.php
https://trac.ffmpeg.org/wiki/Encode/H.264

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

OK, my mp4's don't work on safari mobile, that's a non-starter.
./ffmpeg -i bars.mp4 -c:v libx264 -preset slow -crf 22 -c:a copy bars264.mp4
OK, that particular set of settings don't work on my iPhone...
This is spiralling out of scope of the intent of my test.
Jut one more time:
./ffmpeg -y -i sports_zone.mp4 -c:v libx264 -preset medium -b:v 2600k -pass 1 -c:a aac -b:a 128k -f mp4 /dev/null && \
./ffmpeg -i sports_zone.mp4 -c:v libx264 -preset medium -b:v 2600k -pass 2 -c:a aac -b:a 128k bars2.mp4
make test video, NO SOUND
./ffmpeg -f lavfi -i color=c=red@0.2:duration=5:s=qcif:r=10 red.mp4

In theory you can generate the test tones right from ffmpeg:
./ffmpeg -f lavfi -i "sine=frequency=1000:duration=5" test.wav

