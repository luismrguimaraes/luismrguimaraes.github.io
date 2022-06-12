---
title: Sinc Interpolation
date: 2022-06-11 16:35:00 +0100
categories: [Audio Programming and DSP]
tags: [dsp, graphs]
math: true
---

[digital signal]: https://en.wikipedia.org/wiki/Digital_signal
[analog]: https://en.wikipedia.org/wiki/Analog_signal
[sample-based]: https://youtu.be/cIQ9IXSUzuM?t=379


At some point, I think it's safe to say that every individual studying digital signal processing wondered how a [digital signal] (which is discrete/[sample-based]) was able to accurately represent a sound wave which is continuous.

It turns out that we can **perfectly** reconstruct our continuous [analog] signal using **sinc interpolation**. \\
Here is the sinc function:

$$
\begin{align}
    \DeclareMathOperator{\sinc}{sinc}
    \sinc(x) &= \dfrac{\sin(\pi x)}{\pi x}
\end{align}
$$

I made a graph[^1] that shows the original signal (dark grey), the interpolated signal (blue), as well as the sinc functions centered and scaled at every sample (random colours). 
![](/assets/AudioProgrammingAndDSP/Sinc_Interpolation.png)

If we interpolate using continuous sinc functions centered and scaled at every sample of our digital signal and then sum everything (this is also known as [convolution](https://www.youtube.com/watch?v=QmcoPYUfbJ8)), we get a **perfect** reconstruction of our continuous signal. \
This property is useful if we want to [upsample](https://en.wikipedia.org/wiki/Upsampling) (like we did in the example) and also when converting to the analog domain, which works with continuous signals.

---

[^1]: In this example, the interpolated signal is still a digital signal since we are still working in the digital domain.