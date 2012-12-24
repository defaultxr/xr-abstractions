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

`colors` - outputs a pd color when the left inlet is banged. otherwise, the inlets take floats: from left, the red amount, green amount, and blue amount.

`c` - midi continuous controller interface

`cpuload` - display current CPU load average

`cview` - view all incoming midi CC

`editmode` - (try to) detect edit mode

`inputd` - input accumulator deluxe

`inputn` - input accumulator for numbeers

`input` - input accumulator

`kbdm` - 

`keyboardmidi` - 

`keynum` - 

`keyonchg` - 

`keyonoff` - 

`keyrange` - 

`keyrow` - 

`keysonchg` - 

`kfilename` - abstraction to make paths typed shorter. used by `snd~` and others. **NOTE: you might want to edit this since it uses my paths.**

`khsl` - 

`kspigot~` - 

`kspigot` - 

`mcb` - 

`mck` - 

`m-client` - 

`mcl` - 

`mc` - 

`mct` - 

`mdrums` - 

`mono` - 

`monos` - 

`mspigot` - multi-spigot. has 5 message inlets and allows you to graphically control which of them are mixed to the outlet.

`mstr` - 

`nems` - 

`nkeyb` - 

`nkey` - 

`nknum` - 

`numlock` - 

`nview` - 

`router` - 

`sndsel` - sound selector. allows you to select a sound by browsing folders graphically, because `playlist` kind of sucks. i stole this from someone else's abstractions but i edited it a bit and i plan to redo it from scratch eventually.

`sswitcher~` - 

`switcher~` - 

`switcher` - 

`tview` - text viewer. scrolls the last 5 received inputs.

`wiib` - 

`wiimotec` - 

`wiisring` - 

demos
=====
demonstrations of the included abstractions (definitely open these if you want a tour of this library)

gen
===
abstractions for generating sound

`analogosc~` - 

`analog~` - 

`aphasor~` - 

`fluid~` - 

`grain~` - 

`granular~` - 

`irsong~` - 

`mmo~` - 

`noisef~` - 

`playsf~` - 

`pmosc~` - 

`psndm~` - 

`psndp~` - 

`pulse~` - 

`random~` - 

`randomsong~` - 

`rec~` - 

`recp~` - 

`recsnd~` - 

`sf~` - 

`sine~` - 

`sndcf~` - 

`sndcl~` - 

`sndcm~` - 

`sndcn~` - 

`sndd~` - 

`sndf~` - 

`sndl~` - 

`sndm~` - 

`snd~` - 

`sndp~` - 

`sndrec~` - 

`snds~` - 

`srec~` - 

`timestretch~` - 

`tri~` - 

math
====
abstractions for altering or generating number streams 

`atc~` - "audio to control" - converts a bipolar signal (-1 to 1) to a unipolar signal (0 to 1)

`atc` - "audio to control" - converts bipolar numbers (-1 to 1) to unipolar numbers (0 to 1)

`atr~` - "audio to range" - converts a bipolar signal (-1 to 1) to an arbitrary range specified as arguments or via inlets.

`atr` - "audio to range" - converts bipolar numbers (-1 to 1) to an arbitrary range specified as arguments or via inlets.

`cta~` - "control to audio" - converts a unipolar signal (0 to 1) to a bipolar signal (-1 to 1)

`cta` - "control to audio" - converts unipolar numbers (0 to 1) to bipolar numbers (-1 to 1)

`ctr~` - "control to range" - converts a unipolar signal (0 to 1) to an arbitrary range specified as arguments or via inlets.

`kinv~` - signal inverter. 0 becomes 1, 1 becomes 0, and everything in between.

`kinv` - number inverter. 0 becomes 1, 1 becomes 0, and everything in between.

`kount` - counts up to a certain number and loops, or indefinitely if no argument is given.

`minv` - 

`mrange` - scale 0-127 to an arbitrary range.

`num` - holds a number and allows you to add, subtract, multiply, or divide from that number via messages.

`rangem` - scale a range to midi (0-127).

`rhover` - random numbers hovering around a certain value.

`round` - round a float to the nearest integer.

`rrange` - random within a range (inclusive).

`rtr` - "range to range" - scale one arbitrary range to another arbitrary range.

`transposer` - 

seq
===
sequencer abstractions

`adsr~` - 

`adsr` - 

`amap` - 

`anaseq` - a sequencer made of vertical sliders; supports saving, loading, multiple patterns and more.

`beat~` - 

`boxseq` - 

`bpma` - 

`bpmm2` - 

`bpmm` - metro/gui for outputting bangs on the downbeat, bangs on each quarter note, and numbers for each quarter note. try connecting the third outlet to [anaseq] or [drumseq]

`drumseq` - a 16x4 matrix of toggle boxes. supports saving, loading, multiple patterns and more.

`dust` - 

`edger~` - 

`ft` - 

`iadsr~` - 

`ilist` - 

`kline~` - 

`kline` - 

`listman` - 

`lmap` - 

`lolr` - 

`lolw` - 

`map-help` - 

`map` - 

`numseq` - 

`ometro` - 

`patr` - 

`pattseq` - 

`patw` - 

`pb` - 

`pmap` - 

`rchoice` - 

`rmap` - 

`sbox` - 

`seqfill` - 

`srush` - 

`stack` - 

`taptempo` - 

`td~` - 

`tmap` - 

`tracker` - simple "tracker" sequencer controllable via the keyboard.

`unmap` - 

`vslz` - 

`xeroxer~` - 

utils
=====
miscellaneous utilities

`autosend` - 

`chars` - 

`emptysymbol` - 

`hanning` - 

`hue_to_rgb` - 

`init` - 

`itimer` - 

`ktimer` - 

`lb` - 

`limit~` - 

`listb` - 

`list-find-1` - 

`list-remove` - 

`list-replacer` - 

`list-reset` - 

`lists` - 

`list-without` - 

`marquee` - 

`mod~` - 

`modulation~` - 

`old-init` - 

`o~` - interface for mono output to `dac~`.

`parser` - 

`*+~` - 

`ping` - 

`po~` - panned mono output. same as `o~` but the first argument is the stereo panning position of the input, from -45 to 45.

`porta~` - 

`qtabwrite` - 

`qtimer` - 

`quote` - 

`rporta~` - 

`so~` - interface for stereo output to `dac~`. see also: `o~`.

`spacesym` - 

`span~` - 

`src~` - 

`sreceive~` - 

`ssend~` - 

`sym` - 

`zyn~` -

