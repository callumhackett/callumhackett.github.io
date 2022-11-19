---
# obligatory
layout: page
title: Remastering Jessye Norman # in HTML meta and tab title

# optional, no defaults
permalink: /remastering-jessye-norman # custom page URL, begin with /
tags: ai classical-music mastering mixing plugins # tags for blog posts; space separated
# nav_label: # label to appear in navbar if referenced in _data/navbar.yml

# optional, overrides defaults
type: article # defaults to website, otherwise one of: article, music, video
description: In 1984, Jessye Norman gave an unforgettable live performance of a Poulenc song, though only poor audio survives. Here, I discuss the performance and offer a remastering with notes on my processing setup. # in blog index, HTML meta and social media snippets
image: /assets/images/social/jessye_norman.jpg # path to an image for social media shares, AR 1.9:1, typically 1200x630, begin with /
image_alt: Jessye Norman # description of the social image
---
# Remastering Jessye Norman

There's a song by Poulenc called *Les chemins de l'amour*, which sets a poem about an attempt to remember an act of love in the face of waning memory. The music and text are charming and I often return to them, though "charming" is perhaps all they are --- together, they make touching, memorable salon music but they don't penetrate quite as deeply as other pieces in a similar vein, like Richard Strauss's *Morgen*.

Having said that, there is so much that can be brought to a piece by a performance. There's a video of Jessye Norman singing *Les chemins* live on TV, which I assume was filmed for broadcast but not intended for a CD release. Norman *did* release [an album with *Les chemins*](https://amzn.to/3t1akvO) but the CD version clocks in at just under 4 minutes in length, while her TV performance lasts a whole extra minute. That 25% slow-down makes a huge difference --- you could add an entire movement to a Mozart symphony for that --- and, here, it is an incredible gift. While the CD version is delightful (and probably more in keeping with Poulenc's vision), the TV performance is a breath-taking celebration of Norman's voice; it transforms sweet, lyrical material into a captivating, quasi-meditative experience.

There's no telling how much she may have experimented with her delivery on different occasions --- did she co-ordinate her tempo this time with the pianist (Elisabeth Cooper) beforehand or did she perhaps surprise even herself on the spur of the moment? Cooper's solo introduction is not especially slower than that of the CD, and there is in any case a *ritardando* and pause before the singer's entrance, allowing them to set their own pace, so Norman wouldn't have been led by Cooper. If you watch closely, it seems Cooper was actually ready to go more quickly but soon reined herself in when she noticed Norman's speed. Indeed, in the second half of the song, Norman is so free with rubato, extending some phrases to unpredictable lengths, that Cooper has to watch intensely to follow her breaths and rhythm.

When investigating the origin of the video, I found that, although there are embedded subtitles that translate the song into Spanish, it was most likely aired as an episode of a French TV programme called *Le grand échiquier* in 1984 (Norman also speaks French to the audience at the end). More critically, although there are at least two versions of the video on YouTube, both have poor audio and video quality, as they appear to originate from recording the TV show onto tape. There's not much that can be done about the visuals but I wanted to remaster the audio and upload a new version so that a more pleasant listening experience is available:

{% include youtube.html embed="https://www.youtube.com/embed/V8I0IEwPhrg" %}

Although you can't lift inherently bad audio into studio quality, a few subtle tweaks can get rid of annoyances, thus allowing a performance to shine through. Here are some notes on my process.

## Step 1: Groundwork

My prime motivation was to adjust the balance of the voice but, just as you would sand a piece of wood before varnishing it so that you don't seal in its imperfections, the first thing you want to do with a task like this is identify and remove artefacts that mask the musical content.

In this case, if you listen to [the original video](https://www.youtube.com/watch?v=HarvxxqPjjQ), you can hear several issues:

- Warping (e.g. at 00:37 and 01:17)
- Clipping (e.g. at 2:30)
- Noise/hiss (throughout)
- Electronic hum (throughout)

As far as the warping and clipping are concerned, there's not much you can do about them. These are examples of information **loss** --- the sound that occurred in the studio simply isn't represented in the waveform and is irrecoverable. Technically, there are tools available that offer to adjust audio to 'repair' a clipped signal but these don't restore content, they only make a bad recording more palatable, so in my experience you may as well stick with gain adjustment just to make these artefacts less obnoxious.

Noise and hum, however, are more like layers of dirt that can be rubbed away, albeit not perfectly. In case you're unfamiliar with the difference between them, noise is a full frequency hiss (think of TV static) while hum is a more focused, low frequency spike caused by electrical interference (if you listen to the original video between 00:07 and 00:11, you should be able to hear them both). My go-to tool for removing these is [iZotope's RX software](https://www.izotope.com/en/products/rx.html), which I use most of the time for tidying up home studio recordings.

For removing the hum, I didn't have any information to go on regarding the cause of the interference and the RX module's dynamic tools didn't suggest settings that were any good. However, it's common for hum to be centred on 50Hz or 60Hz and I found that setting the de-hum to 50Hz produced a marked improvement.

As for de-noising, depending on the task in hand, I often lean towards applying that first, typically because it has the most consistent spectral profile, so it can be easily targeted, and getting rid of it early prevents other adjustments from reinforcing it. However, modifications like these are always sensitive to the order in which they are applied and, on this occasion, I wanted to wait until after Step 2 to remove the noise, for reasons I explain below.

## Step 2: Reverse-Engineered Tracking

In an ideal remastering scenario, you wouldn't be dealing with a final stereo mix; you'd have the original stems so that you could isolate (e.g.) the voice, piano and studio audience. Of course, these were unavailable for this video but, thanks to advances in machine learning techniques, you can use something like [Steinberg's SpectraLayers](https://www.steinberg.net/spectralayers/) to separate a full mix into its original parts.

There are limitations to what SpectraLayers can do --- you can't arbitrarily ask it to isolate anything you like --- but one of the things it does extremely well is separate vocals from everything else. It can in principle separate a piano as well, though it wasn't particularly effective at doing this for this audio --- I expect because the piano was originally recorded quite badly and SpectraLayer's algorithm is not suited for dealing with such low fidelity --- but, for this piece, it wasn't necessary anyway. Given that the piano part is just what's left when you subtract the voice from the mix and ignore the audience noise, it was adequate mix with the isolated voice and the remainder of the signal.

Here's a clip of the extracted vocal stem before any further processing. You can clearly hear some piano bleed where the algorithm misidentifies it as voice content but, most importantly, almost all of the voice was correctly captured in this track:

{% include audio.html file="/assets/audio/isolated-voice.mp3" %}

To perform this isolation, there's a sensitivity setting for each layer --- the higher the sensitivity, the more of the input audio is likely to be included in the layer's output. For the voice, it was clear that a higher sensitivity would capture more of its high frequency content but it would also bring high frequency noise with it. This is a trade-off that has to be dealt with based on the specific material you're processing.

Here, looking ahead to mixing the voice after isolating it, I knew I'd need a significant boost to the high end and I wanted to do this without boosting noise along with it, so I opted for a middling sensitivity that left almost all noise out of the vocal stem, at the expense of some small loss of high frequency content. As it happens, the original recording didn't capture much of the voice's high end to begin with, so the trade-off wasn't so severe and I might have made a different choice in different conditions.

This brings me back to why I wanted to wait until this piece of processing was complete before de-noising with RX, as I could have been tempted to do the noise removal first, so that I could use a higher sensitivity setting on the voice without bringing any noise through. Well, when you apply noise removal, if you push it too hard, you inevitably lose musical content as well because of the way the noise is baked into the whole spectrum of the track. As there was so much noise in this recording, if I had applied as much noise removal as I wanted before isolating the voice, it would have eliminated the voice's high frequency content before SpectraLayers even had a chance to isolate it. Conversely, by letting SpectraLayers isolate the voice first --- trusting its algorithm to identify all of the good high frequency stuff worth keeping --- I could apply more liberal noise removal to the remaining signal without affecting the voice at all.

But again, there was a trade-off lurking here. By opting to isolate the voice before noise removal, this had the knock-on effect of pushing the noise into the leftover piano stem, meaning that the piano's character might still be sacrificed with noise removal pused too hard. While in some cases this would have made me prefer to de-noise everything equally up front, I knew that the piano sound was already much poorer than the voice's, so I chose to keep the voice as pristine as possible and let the piano suffer the brunt of the processing because its degradation would be relatively negligible.

When running the de-noiser, I still couldn't push it to its limits without problems, so, given some residual noise that was difficult to remove, I also put a gate on the mix just for the introduction before the song begins, so that the noise would be less obvious during studio silence (I bypassed the gate for the rest of the song, as there were no noisy silences during it and having the gate running would only risk unwanted side effects). I still set the gate to let just a little noise through, though, as having dead silence at any moment would have sounded artificial.

## An Aside on AI Tools

As we're seeing more and more machine learning algorithms being used for automated media enhancement, I thought it would be worth exploring their usefulness for a project like this. I knew there was no hope of feeding a piece of software the original unprocessed audio and getting an instant remaster because the needs of the track were just too complex but I was intrigued at the possibility of using something like the Spectral Recovery component of iZotope's RX to add some detail to the voice after I'd isolated and tidied it up. In the end, RX basically didn't achieve anything except accentuate the mid-range and boost the noise, but in fairness this is not the use case envisioned for the product. Yet another reminder that you can't fix in a mix what was never recorded to begin with.

## Step 3: Rebalancing

With isolated vocals in hand, the next task was to decide how to mix them. With audio of this low quality, I think it's important to aim to be subtle and to not give into the temptation to shape it so much that you risk inauthenticity. Always remember that human attention adapts very well to all sorts of background noise, so there's no need to be heavy-handed to improve a listener's experience.

The most obvious and necessary tool in this case was EQ. The voice benefited a lot from a shelf boosting the high frequencies and it tolerated a fairly high level, given that SpectraLayers had isolated the voice almost without noise. There was a boxiness in the original sound that was made a little clearer with a reduction at around 500Hz and I did some very light shaping between 800-2000Hz to remove some nasality at the lower end and lift some of the body at the upper end. These are standard treatments for voice recordings.

For the piano track, there was still so much noise left over --- and so little of the piano's own high frequency content --- that I went quite hard on a couple of low-pass filters to really clamp down on the hiss. I also reduced the same boxiness at around 500Hz but otherwise there was little point processing the track further. There was so little detail in the tone of the piano that a boost here or a cut there might make it sound different, but nothing was going to make it sound obviously better.

After setting up the EQ parameters, I wondered whether I wanted to do any other processing at all (e.g. compression, saturation, even reverb?), in case I might get carried away and go beyond the limits I'd set myself. I had deliberately stayed away from analogue emulation EQs, as I didn't want the track to sound as if additive effects had been applied but, being fairly limited in what I could achieve with EQ, I decided some *very* minor and highly targeted saturation and reverb might be useful, as, using methods like these, you can add body to a signal in a way that you can't otherwise when the original material is lacking.

My current saturation plug-in of choice is [Spectre from Wavesfactory](https://www.wavesfactory.com/audio-plugins/spectre/). Here, I found the voice was clarified by slightly reducing my EQ's high shelf and replacing it with a small amount of high frequency tube saturation, as well as a small bump in the low-mids. With a similar logic, I experimented with a few different approaches to reverb. I began with [Soundtoys Little Plate](https://www.soundtoys.com/product/little-plate/), which I like a lot, but, though it did suit Norman's voice, the reverb tail came through too strongly at the ends of phrases even on the lowest mix settings. With this in mind, I switched to a plate setting on [Exponential Audio's R4](https://www.izotope.com/en/shop/exponential-audio-r4.html), as I knew that it had a parameter to cut the tail short. R4 sounds excellent but it also suffers sometimes from being too powerful, and I decided to discard this option when I felt that there were too many parameters worth adjusting. So, in the end, I used a convolution reverb with one of my favourite impulse responses, turning the early reflections down and dialling it in just enough so that the tail was barely noticeable.