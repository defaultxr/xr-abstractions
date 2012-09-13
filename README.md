defaultxr's pure data abstractions
==================================

this is a collection of pure data abstractions i've made. i don't use pd as much as i used to but this is probably the place where you'll find the latest versions of all my stuff.

please notify me if you get any "not found" errors while you're using any of these (i may have forgotten to include some of them).

hopefully the comments in each one will be useful to you. below is a very incomplete overview of the contents of this library. i'll document it more in the future, maybe.

ctrl
====
abstractions for controlling things

demos
=====
demonstrations of the included abstractions (definitely open these if you want a tour of this library)

gen
===
abstractions for generating sound

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