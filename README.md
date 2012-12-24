defaultxr's pure data abstractions
==================================

this is a collection of pure data abstractions i've made. i don't use pd as much as i used to but this is probably the place where you'll find the latest versions of all my stuff.

please notify me if you get any "not found" errors while you're using any of these (i may have forgotten to include some of them in the repository).

hopefully the comments in each one will be useful to you. below is an overview of the contents of this library.

analysis
========
abstractions for analyzing stuff or displaying information from audio signals.

`attacks~` - supposed to generate a list of a sound file's 'attacks', which could then be used for `snds~`. WIP.

`ifiddle~` - graphical interface to fiddle~.

`scroll~` - scrolling amplitude view.

`siga~` - signal analysis. shows the current value, average value, maximum and minimum values, and a `vsl` to plot the input. there is also a `bng` to reset the recorded maximum and minimum.

`signum~` - current value of the signal. basically like `unsig~` with a number box gui.

`spectrum~` - shows the FFT spectrum of the input.

`vcsig~` - view control signal. shows the current value of an input signal graphically. assumes the signal is between 0 and 1.

`view~` - waveform view.

`vsig~` - view signal. same as `vcsig~` but assumes the input range is between -1 and 1.

ctrl
====
abstractions for controlling things, either via keyboard or by clicking.

`bswitcher~` - graphically switches between 2 audio inputs. there are 3 inlets: the middle is a message inlet accepting floats to select the input to send to the outlet, while the left and right inlets are the audio inputs.

`capslock` - shows whether capslock is on or off and also outputs 1 or 0 depending.

`cb` - control bend. shows the current value of the MIDI bend parameter, also adjusting its range to 0-127.

`cnum` - control number. use your keyboard's numpad to increase or decrease a number. use 8 to increase it or 2 to decrease it. probably won't work if your numlock is on.

`colors` - 

demos
=====
demonstrations of the included abstractions (definitely open these if you want a tour of this library)

gen
===
abstractions for generating sound

math
====
abstractions for altering or generating number streams 

seq
===
sequencer abstractions

bpmm - metro/gui for outputting bangs on the downbeat, bangs on 16th notes, and numbers for each 16th note. try connecting the third outlet to [anaseq] or [drumseq]

anaseq - a sequencer made of vertical sliders; supports saving, loading, multiple patterns and more.

drumseq - a 16x4 matrix of toggle boxes. supports saving, loading, multiple patterns and more.

tracker - simple "tracker" controllable via the keyboard.

utils
=====
miscellaneous utilities

atr~, atr, atc~, atc, cta~, cta, ctr~, rtr - convert inputs from one range to another (i.e. atc~ converts audio from the range (-1 to 1) to the range (0 to 1); cta~ does the reverse; atr~ converts audio from the range (-1 to 1) to an arbitrary range specified as arguments)

o~, so~, po~ - abstractions for audio output, stereo output, and panned output, respectively.