---
title: Retro Sound
date: 2025-10-30 22:18:00 +0000
categories: [Music, Sound Design]
tags: [music, sound_design]
math: true
---

### Context

This post is about retro music and sound design I recently did. I had worked previously on a [project evoking retro themes](https://hail-seitan.itch.io/unstable-rob), but we didn't really feel comfortable embracing the restrictions of the hardware from the earlier days. Heck, I don't even do now, but there is a difference between _evoking retro themes_ and _making retro sounds_.

My recent experience was motivated by [this contest](https://kilohearts.com/blog/kilohearts_game_audio_week_contest_2025) from Kilohearts, which asked the participants to "Create \[their] own original audio", focusing on sound effects, for the following video:

<!--![](../../assets/videos/data_man_clip.mp4)-->

<div style="text-align: center;">
<video src="/assets/videos/data_man_clip.mp4" width="512" height="480" controls></video>
</div>

I basically ignored the "focusing on sound effects" part, and decided to imagine and create a whole soundscape for this game, as believable as I could make it, with the little experience I had with retro music and retro sound.

### The "Retro Sound"

Since the game ([Data Man](https://darkbitsgames.itch.io/data-man)) can run on the NES, I started by finding software that could create emulated NES sound, or better yet, play on the actual hardware. I found [FamiStudio](https://famistudio.org/) that is able to do exactly that! At first, it was a bit difficult to figure out some crucial features like playing imported samples, and later, after asking for help on the Discord server, I learned that the documentation I was referring to was actually outdated... But after learning the basic features, the software is very pleasurable to work with because of its simplicity, decent amount of keyboard shortcuts and quality of life features like the special paste system.

The NES sound chip, without any expansions, has 5 audio channels: two squares, often used as first and second voices; one triangle, often for bass; a noise channel; and a delta modulation channel (DMC) which is able to play audio samples. The DMC can play audio samples encoded as 1-bit deltas that tell a 7-bit PCM counter to increase (1) or decrease (0) (referred to as DPCM) or play 7-bit PCM audio directly. The second option requires more storage and more CPU power, so the first one is most often used.\
With DPCM, each sample still has $2^{7\ bits} = 128$ of possible values while being stored with just $2^{1\ bit} = 2$, resulting in 7 times less storage (read more [here](https://www.emulationonline.com/systems/nes/apu-audio/#dmc)). This, of course, has an impact on sound quality but also contributes to creating a _retro sound_. The following is a capture of a sine wave imported into FamiStudio, which shows how a sine wave looks like after DPCM decoding:
![](/assets/img/DPCMSine.jpg)

I first decided to use the noise and DMC channels for the sound effects, so I started creating the music with the other 3 (squares and triangle). The triangle is used for the bassline and the squares for the lead and accompaniment. Then, I added the sound effects: the fire and the beam use the noise channel, but because they play for a long time, I have to use the DMC for the other SFX. I imported the samples in a WAV format into FamiStudio to convert them into DPCM and then recorded them into Reaper so that I could more easily sync the SFX with the video. But, I made sure no two SFX from the same channel were playing at once, because that is not possible in the actual hardware. Later on, I also added some percussion to the music using the noise channel, but every time the SFX plays, the percussion is interrupted.

Here is the clip with the SFX:
{% include embed/youtube.html id='zAeXSzTtZfA' %}
And here is the music alone:
{% include embed/youtube.html id='b9enqsFeBo8' %}

### Conclusion

Each day I feel more confident that limitations breed creativity. I really enjoyed discovering what can be done with a retro sound chip, which despite its clear limitations, still allow for a great level of variability. In contrast, being unbounded by the infinite possiblities a DAW provides, can often make creative decisions more difficult because whenever you are choosing from an infinite set of options, it's very unlikely you'll make the best possible choice, and we always want our music to sound the best it possibily can.

### References

- https://www.emulationonline.com/systems/nes/apu-audio/
- https://www.nesdev.org/wiki/APU
- https://en.wikipedia.org/wiki/Ricoh_2A03
- https://famistudio.org/
- https://darkbitsgames.itch.io/data-man
- https://kilohearts.com/blog/kilohearts_game_audio_week_contest_2025
