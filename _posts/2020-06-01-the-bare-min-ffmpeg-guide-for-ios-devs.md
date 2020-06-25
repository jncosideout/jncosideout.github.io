---
title: The Bare Minimum Guide to ffmpeg For iOS Devs
tags: [ffmpeg, iOS, xcode tools]
date: 2020-06-01
---
## How to record simulator video and format for App Store Previews
<h3 id="xcrun-simctl-record">1. Record from the simulator</h3>
- - -
{% highlight shell %}
xcrun simctl io booted recordVideo --codec=h264 --force iPhone8Plus_vsCo-BG3.mp4
{% endhighlight %}
- output will be **portrait**

Using the iPhone 8 Plus 5.5” simulator, the video was 1242 × 2208 (iPhone 8 Plus native resolution) and for me, the frame rate was 44fps. This may be due the performance of the simulator for the iPhone 8 Plus. I found out later when recording for 6.5" resolution that my 11 Pro Max simulator rendered at a much lower 18 fps when running the same app on the same functionality.

I am using Xcode 11 but I found that [people were complaining about the speed of simulators in Xcode 10.](https://developer.apple.com/forums/thread/108668). So try running your app on different simulators and use the settings on the simulator to find the fps. It may vary and you'll need to change it in ffmpeg.

<h3 id="change-frame-rate">2. Change the Frame rate (fps)</h3>
- - -
Run ffmpeg to force changing frame rate to, 24 fps, for example.
{% highlight shell %}
ffmpeg -i input.mp4 -r 24 output.mp4
{% endhighlight %}
- Source: [Using ffmpeg to change framerate](https://stackoverflow.com/a/45465730/8658897)

<h3 id="rotate">3. Rotate the video</h3>
- - -
portrait -> landscape
{% highlight shell %}
ffmpeg -i in.mov -vf "transpose=2” out.mov
{% endhighlight %}

For the transpose parameter you can pass:

+ 0 = 90 Counter Clockwise and Vertical Flip (default)
+ 1 = 90 Clockwise
+ 2 = 90 Counter Clockwise
+ 3 = 90 Clockwise and Vertical Flip

Source: [*Rotating videos with FFmpeg*](https://stackoverflow.com/a/9570992/8658897)

<h3 id="change-dimensions">4. Change the scale</h3>
- - -
You can get the dimensions of your input video like this:
{% highlight shell %}
ffprobe -v error -of flat=s=_ -select_streams v:0 -show_entries stream=height,width in.mp4
{% endhighlight %}
You can also use ffprobe to find all other properties of your input file
- Source: [How do I use ffmpeg to get the video resolution?](https://superuser.com/questions/841235/how-do-i-use-ffmpeg-to-get-the-video-resolution)

If we'd like to keep the aspect ratio, we need to specify only one component, either width or height, and set the other component to -1. For example, this command line:
{% highlight shell %}
ffmpeg -i input.jpg -vf scale=320:-1 output_320.png
{% endhighlight %}
- Source: [FFmpeg wiki: Scaling](https://trac.ffmpeg.org/wiki/Scaling)

...will set the width of the output image to 320 pixels and will calculate the height of the output image according to the aspect ratio of the input image. The resulting image will have a dimension of 320⨉207 pixels.

Some codecs require the size of width and height to be a multiple of n. You can achieve this by setting the width or height to -n:
{% highlight shell %}
ffmpeg -i input.jpg -vf scale=320:-2 output_320.png
{% endhighlight %}

The output will now be 320⨉206 pixels.

<h3 id="get-frame-rate">5. Get metadata, frame rate</h3>
- - -
Get all metadata
{% highlight shell %}
ffmpeg -i input.jpg
{% endhighlight %}

Filter metadata for  frame rate only
{% highlight shell %}
ffmpeg -i filename 2>&1 | sed -n "s/.*, \(.*\) fp.*/\1/p"
{% endhighlight %}
\* [Understanding Shell Script's idiom: 2>&1](https://www.brianstorti.com/understanding-shell-script-idiom-redirect/)

\* [A Sed and Awk Micro-Primer](https://www.tldp.org/LDP/abs/html/x23170.html)
<!-- markdown thinks the rest of the file should be italics from here on, but the final html will not be -->

- Source: [How to find frames per second of any video file?](https://askubuntu.com/questions/110264/how-to-find-frames-per-second-of-any-video-file)

<h3 id="combine-filters">6. Put it all together</h3>
- - -
To avoid re-encoding you can do all the above on one line
{% highlight shell %}
ffmpeg -i input.mp4 -vf "transpose=2, scale=1920:-2" -r 24 output.mp4
{% endhighlight %}
- Source: [Applying multiple filters at once in ffmpeg](https://superuser.com/questions/586045/applying-multiple-filters-at-once-in-ffmpeg)
- Source: [FFmpeg Filtering Guide](https://trac.ffmpeg.org/wiki/FilteringGuide)

<h3 id="add-silence">7. Add silent audio track afterward</h3>
- - -
You probably can combine the following command with the last one but it is complicated. I think the reason is that the "putting it all together" command above is [applying a video filter, and the command below is using the copy stream filter][video filter copy stream] for video. However, if you are worried about re-encoding and losing video quality, here is a way to just encode the audio track, and just copy the video track without re-encoding it.

Most people write apps with sound but mine has none. Apple will reject your submission if it doesn't have an audio track so you can add silence.

{% highlight shell %}
ffmpeg -f lavfi -i anullsrc=channel_layout=stereo:sample_rate=44100 -i preview.mp4 \
-shortest -c:v copy -c:a aac previewWithSilence.mp4
{% endhighlight %}
**Note: Windows users should use `^` instead of `\` for multi-line commands.**
- Source: [ios - App Preview submission, video has audio that is not two-channel](https://stackoverflow.com/a/45983435)

<h3 id="cutting">8. Cutting video</h3>
- - -
Most video files have key frames that are like bookmarks at points in time in the video.

If you want to cut precisely starting at a non-keyframe and want it to play starting at the desired point on a player that does not support edit lists, or want to ensure that the cut portion is not actually in the output file then you can do that by re-encoding so that there will be a keyframe precisely at the desired start time. Re-encoding is the default if you do not specify copy. For example:

-t is total time
{% highlight shell %}
ffmpeg -i movie.mp4 -ss 00:00:03 -t 00:00:08 -async 1 cut.mp4
{% endhighlight %}
- Source: [Cutting the videos based on start and end time using ffmpeg](https://stackoverflow.com/questions/18444194/cutting-the-videos-based-on-start-and-end-time-using-ffmpeg)

#### Example of time snipping including rotation to landscape and a scale filter for dimensions
{% highlight shell %}
beaty$ ffmpeg -i iPhone8Plus_vsOnlineReplayWrapAroundCapture-noBG.mp4 -ss 00:00:06 -t 00:00:26 -async 1 -vf "transpose=2, scale=1920:-2" -r 24 iPhone8Plus_vsOnline_silenced_lowFPS_rotated_-noBG.mp4
{% endhighlight %}

<h3 id="repeat-last-frame">9. Repeat last frame in video using ffmpeg</h3>
- - -
A few of my videos were a few fractions of a second short to be accepted by Apple. So I just repeated the last frame in the video a few times to make up the time.

{% highlight shell %}
ffmpeg -i in.mp4 -vf tpad=stop_mode=clone:stop_duration=2 out.mp4
{% endhighlight %}
**Note: Audio is ignored in the above method.**
- Source: [Repeat last frame in video using ffmpeg](https://stackoverflow.com/questions/43414641/repeat-last-frame-in-video-using-ffmpeg)

<h3 id="bitrate-ffmpeg">10. Bitrate Constant Rate Factor (CRF)</h3>
***
You probably won't need this but you can play around with the video quality this way:

Use this rate control mode if you want to keep the best quality and care less about the file size. This is the recommended rate control mode for most uses.

From FFmpeg wiki:
>This method allows the encoder to attempt to achieve a certain output quality for the whole file when output file size is of less importance. This provides maximum compression efficiency with a single pass. By adjusting the so-called quantizer for each frame, it gets the bitrate it needs to keep the requested quality level. The downside is that you can't tell it to get a specific filesize or not go over a specific size or bitrate, which means that this method is not recommended for encoding videos for streaming.

#### CRF Example
This command encodes a video with good quality, using slower preset to achieve better compression:
{% highlight shell %}
ffmpeg -i input.avi -c:v libx264 -preset slow -crf 22 -c:a copy output.mkv
{% endhighlight %}

- Source: [FFmpeg wiki: H.264 Video Encoding Guide](https://trac.ffmpeg.org/wiki/Encode/H.264)

<h3 id="macos-sar-scaling">11. Changed the resolution to required dimensions, still gets rejected from Apple</h3>
***
I spent hours banging my head against the wall, trying every combination of filters I could think of to resize my videos. At some point you need to ask yourself "Is it really me? Or am I being misled?"

The problem below matches the one I encountered while formatting videos made with xcrun and the 11 Pro Max simulator:

*Question:* I need to generate another video with the resolution 1920x886 for supporting 6.5" devices,
so I used the following command to perform the scaling:
{% highlight shell %}
ffmpeg -i video_1920_1080.mp4 -vf scale=1920:886 -c:a copy video_1920_886.mp4
{% endhighlight %}
1.	ffmpeg -i tells me the video is in the resolution 1920x886.
2.	macos file properties tells me the video is in the resolution 1575x886.
3.	VLC tells me the video has a Resolution of 1920x898 and a Display Resolution of 1920x886.

Why are there three different resolutions? How can I change each one of them? I suppose the App Store Connect website expects the file properties resolution to be 1920x886. How can I change that?

*Answer:*
FFmpeg's scale filter will adjust the sample aspect ratio of the video so that the original display ratio is preserved. Apple, apparently, computes the new effective display resolution using that SAR.

Insert a setsar filter to reset the SAR to 1, so that the display resolution is the same as the stored resolution.
{% highlight shell %}
ffmpeg -i video_1920_1080.mp4 -vf scale=1920:886,setsar=1 -c:a copy video_1920_886.mp4
{% endhighlight %}
- Source: [Using ffmpeg to scale app preview videos for the AppStore](https://stackoverflow.com/questions/53573468/using-ffmpeg-to-scale-app-preview-videos-for-the-appstore)

[video filter copy stream]: https://stackoverflow.com/questions/53518589/how-to-use-filtering-and-stream-copy-together-with-ffmpeg
