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

`inputn` - input accumulator for numbers

`input` - input accumulator

`kbdm` - 

`keyboardmidi` - 

`keynum` - get numbers from the keyboard. if "h" is provided as the first argument, also allows hexadecimal numbers (a-f).

`keyonchg` - 

`keyonoff` - 

`keyrange` - 

`keyrow` - 

`keysonchg` - 

`kfilename` - abstraction to make paths typed shorter. used by `snd~` and others. **NOTE: you might want to edit this since it uses my paths.**

`khsl` - 

`kspigot~` - graphical audio spigot (left inlet is for the audio, right inlet is to open or close the spigot)

`kspigot` - graphical message spigot (left inlet is for the messages, right inlet is to open or close the spigot)

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

`numlock` - shows whether numlock is on or off and also outputs 1 or 0 depending.

`nview` - view all incoming midi note values.

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

`analog~` - analog simulation. basically supposed to be like line noise and a small dc offset. probably not a very good simulation of the actual analog sound.

`aphasor~` - bipolar version of `phasor~`

`fluid~` - FluidSynth (SoundFont) interface.

`grain~` - 

`granular~` - 

`irsong~` - interface to `randomsong~`

`noisef~` - noise frequency

`playsf~` - play a file from the argument.

`pmosc~` - phase modulation oscillator, stolen from PDX7, with a slight modification.

`psndm~` - polyphonic sound player, using midi notes for melodies. this needs work.

`psndp~` - polyphonic sound player. similar to `sndp~` but with 8 voices.

`pulse~` - non-band-limited pulse wave with modulatable pulse width.

`random~` - random wave generator (based on a LADSPA plugin).

`randomsong~` - play a random song from your hard drive (you'll probably have to modify this a lot for it to work for you)

`rec~` - record a snippet of sound to a table.

`recp~` - play the a snippet of sound from `rec~`.

`recsnd~` - allows access to the sound recorded with `rec~` in a similar manner to the way `snd~` allows.

`sine~` - extremely simple sine wave oscillator based on `phasor~` and `cos~`. might change this in the future.

`sndcf~` - generates a signal to control `snd~` based on frequency of the sound.

`sndcl~` - generates a signal to control `snd~` based on a `line~` (i.e. with start and end-points and a rate)

`sndcm~` - generates a signal to control `snd~` based on midi numbers (60 being the base note)

`sndd~` - sound duplicate. like `snd~` but does not re-load the file; simply re-uses the table containing the already-loaded file.

`sndf~` - sound frequency. play a sound at a rate multiplied by the normal rate.

`sndl~` - sound line. play a sound or snippets of it based a `line~`.

`sndm~` - sound midi. play a sound based on midi note numbers, with 60 being the default base note.

`snd~` - sound file. load a sound into a table and read through it via the audio inlet, with 0 being the beginning and 1 being the end.

`sndp~` - sound play. load a sound into a table and bang to play the whole sound. good for drums.

`snds~` - sound slices. play snippets of a sound that has been analyzed by `attacks~`

`srec~` - signal-based `rec~`. work-in-progress.

`timestretch~` - "timestretch" a sound by repeatedly going back and forth through it.

`tri~` - non-band-limited triangle or saw wave.

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

`maybe` - 

`minv` - 

`mrange` - scale 0-127 to an arbitrary range.

`num` - holds a number and allows you to add, subtract, multiply, or divide from that number via messages.

`rangem` - scale a range to midi (0-127).

`round` - round a float to the nearest integer.

`rrange` - random within a range (inclusive).

`rtr` - "range to range" - scale one arbitrary range to another arbitrary range.

`transposer` - 

seq
===
sequencer abstractions

`adsr~` - attack decay sustain release envelope... well, kinda.

`adsr` - same as `adsr~`, but outputs messages instead of audio signal.

`amap` - advanced version of `map`. has more features like random selection, insertion, deletion, and dumping the contents.

`anaseq` - a sequencer made of vertical sliders; supports saving, loading, multiple patterns and more.

`beat~` - 

`boxseq` - 6x6 "box" sequencer. can be played in any direction, even diagonally. was an experiment. might change it later.

`bpma` - 

`bpmm2` - was supposed to be the next version of `bpmm` with fewer outlets but i might delete this actually.

`bpmm` - metro/gui for outputting bangs on the downbeat, bangs on each quarter note, and numbers for each quarter note. try connecting the third outlet to `anaseq` or `drumseq`

`drumseq` - a 16x4 matrix of toggle boxes. supports saving, loading, multiple patterns and more.

`dust` - 

`edger~` - 

`ft` - 

`iadsr~` - 

`ilist` - 

`kline~` - 

`kline` - 

`listman` - list manager. you can add elements to a list, remove them, check for their existence within the list, etc. you can't remove by index, only by value, so don't use this if you want to have multiple of the same element.

`lmap` - 

`lolr` - 

`lolw` - 

`map` - map bangs or floats to elements of a list provided as arguments or set via the right inlet. probably the most useful abstraction you'll ever find.

`ometro` - "on metro". a `metro` that is on by default.

`patr` - 

`pattseq` - graphical sequencer similar to `drumseq` but outputs numbers rather than just bangs.

`patw` - 

`pb` - processor for betablocker. basically a little computer.

`pmap` - program map. related to `pb`.

`rchoice` - random choice from either the arguments, or from the incoming list.

`rmap` - 

`sbox` - 

`seqfill` - 

`srush` - "snare rush" abstraction. might redo this to make it simpler.

`stack` - a stack. you can push things onto the stack or pop them off of it.

`taptempo` - tap or send bangs to get the tempo.

`td~` - 

`tmap` - timed map that plays through the whole list with one bang.

`tracker` - simple "tracker" sequencer controllable via the keyboard.

`unmap` - get the index of incoming values in a list provided either as arguments or via the right inlet. the opposite of `map`. 

`vslz` - 

`xeroxer~` - 

synths
======
"full-featured" synthesizers. a lot of these are scrapped designs or ripped from other people (although i've given credit). most of these aren't that great.

`Adder4~` - scrapped

`Adder~` - scrapped

`Adder_voice~` - scrapped

`filters~` - scrapped

`fmFeedback~` - FM feedback synth stolen from NoizeHack, slightly modified by me.

`kick1~` - extremely basic kick drum synth

`kick2~` - another extremely basic kick drum synth

`oscs~` - scrapped

`snare1~` - extremely basic snare drum synth

`snare2~` - another extremely basic snare drum synth

`Synf~` - scrapped

`tb303~` - TB303 clone. work-in-progress. probably doesn't sound much like the real thing.

utils
=====
miscellaneous utilities

`autosend` - 

`chars` - separate a symbol into a list of its characters.

`emptysymbol` - test if a symbol is the empty symbol.

`hanning` - hanning window.

`hue_to_rgb` - 

`itimer` - 

`ktimer` - 

`lb` - `loadbang` abstraction. lets you output a specific number or value on load, rather than just a bang.

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

`o~` - interface for mono output to `dac~`.

`parser` - 

`*+~` - 

`ping` - 

`po~` - panned mono output. same as `o~` but the first argument is the stereo panning position of the input, from -45 to 45.

`porta~` - portamento. might need work.

`qtabwrite` - 

`qtimer` - 

`quote` - 

`rporta~` - relative portamento. might need work.

`so~` - interface for stereo output to `dac~`. see also: `o~`.

`spacesym` - outputs a symbol that has a character that looks blank. thus, you can make symbols with "spaces" in them without them being lists. it's one of pd's quirks. don't know if this'll work everywhere.

`span~` - simple panner. like `pan~` but lets you specify the panning position as an argument if you're lazy.

`src~` - 

`sreceive~` - 

`ssend~` - 

`sym` - 

`zyn~` -

