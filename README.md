defaultxr's Pure Data Abstractions
==================================
This is a collection of abstractions I've made for Pure Data. It includes sequencers, GUIs, general utilities, and a few effects and synths. I'm still in the process of writing them, so consider them "beta", and expect changes if you upgrade later (which will hopefully be mentioned in commit messages). Some objects might get renamed, removed, or end up working/looking completely different later. Beware of this.

Right now, most of these abstractions will probably only work under Pd-extended 0.43. Since Pd-extended is no longer maintained, I'll slowly be working towards Pd-vanilla compatibility for this library.

Please notify me of any bugs you find while using these abstractions.

Some of the abstractions I find most useful:
* `map` - easy list access (useful for arpeggios, patterns, etc.)
* `snd~` - easy sound file access (provide a filename as the first argument and it is automatically handled for you)
* `o~` - easy `dac~` access (with volume control, keyboard shortcuts, etc)
* `view~` - view the waveform (acts as a simple oscilloscope)
* `drumseq2` - simple and easy step sequencer (soon to be renamed to either just `drumseq` or `ds`. the original `drumseq` (still included) is now deprecated so don't use it!)
* `rrange` - random range. easy way to get an integer within a specific range.
* `rchoice` - random choice. choose randomly from a list provided as arguments or to the right inlet.
* `bpmm` - clock for use with sequencers like `drumseq`, `anaseq`, etc.
* `tb303~` - fake tb303 (simple and quick synth)
* `rmap` - receive map (quickly create a lot of `receive` objects just by specifying them as arguments to `rmap`)
* `unmap` - map inputs to their indexes in a list (the inverse of `map`)
* `tview` - GUI view of incoming messages

Requirements
============

Here's a list of the libraries that this one depends on. All of these should be installed automatically if you're using Pd 0.48

* cyclone
* iemguts
* motex
* zexy

Installation
============

After you install the requirements listed above, the abstractions should "just work". However there are a few that you may want to edit:

* `kfilename` - this abstraction is used to shorten filenames. So for example, `~` is replaced with `/home/modula` by default. You will most likely want to change that so that it points to your home directory instead.

Overview
========
Below is an overview of all of the included abstractions.

ctrl
----
abstractions for controlling things, either via keyboard or by clicking.

* `ca` - FIX

* `capslock` - shows whether capslock is on or off and also outputs 1 or 0 depending.

* `cb` - control bend. shows the current value of the MIDI bend parameter, also adjusting its range to 0-127.

* `cnum` - control number. use your keyboard's numpad to increase or decrease a number. use 8 to increase it or 2 to decrease it. probably won't work if your numlock is on.

* `c` - midi continuous controller interface

* `crossfade~` - graphical "crossfader". see also: `scrossfade~`

* `editmode` - detect whether edit mode is on or off.

* `inputd` - input accumulator deluxe

* `inputn` - input accumulator for numbers

* `input` - input accumulator (similar to the `symbol` atom, but without a built-in GUI)

* `ispigot~` - graphical audio spigot (left inlet is for the audio, right inlet is to open or close the spigot)

* `ispigot` - graphical message spigot (left inlet is for the messages, right inlet is to open or close the spigot)

* `kbdm` - convert numbers from `key` into midi note numbers so you can use your keyboard to play notes.

* `keydrum` - use squares of the keyboard as drum pads.

* `keynum` - get numbers from the keyboard. if "h" is provided as the first argument, also allows hexadecimal numbers (a-f).

* `keyonchg` - outputs a bang when the $1 key is pressed.

* `keyonoff` - outputs 1 when the $1 key is pressed and 0 when it is released.

* `keyrow` - converts numbers from `key` into the numbers 0-9. in other words, use a row of keys as numbers.

* `kfilename` - abstraction for making paths. used by `snd~`, `drumseq`, `anaseq` and others.

* `mono` - monosynth implementation (keeps track of which keys are held down, only sending the most recent, including if more than one has been pressed/held down)

* `monos` - simpler version of mono. should work better with synths expecting input from something like `notein`.

* `mspigot` - multi-spigot. has 5 message inlets and allows you to graphically control which of them are mixed to the outlet.

* `mstr` - master. don't use it. i'll make a better version eventually, maybe.

* `nems` - non-edit mode spigot. only allows messages to pass when edit mode is off.

* `numlock` - shows whether numlock is on or off and also outputs 1 or 0 depending.

* `polys` - similar to pd's built-in `poly` but allows you to specify a specific voice with note-offs (i.e. so you can have multiple voices with the same note). WIP: voice stealing is not yet implemented.

* `router` - routes one input (left inlet) to either the left or right outlet, depending on the state of the ratio control. the right inlet allows you to switch the outlet.

* `scrossfade~` - graphical stereo "crossfader". see also: `crossfade~`

* `sndsel` - sound selector. allows you to select a sound by browsing folders graphically, because `playlist` kind of sucks. it's a work-in-progress, but it's probably ready for regular use.

* `switcher~` - graphically switches between 2 audio inputs. there are 3 inlets: the middle is a message inlet accepting floats to select the input to send to the outlet, while the left and right inlets are the audio inputs.

* `switcher` - switches between outputting the left inlet or the right inlet graphically via a ratio control. you can also change the inlet by sending a "switch" message to the first inlet.

demos
-----
demonstrations of the included abstractions (definitely open these if you want a tour of this library)

fx
--
abstractions for many LADSPA effects, as well as interfaces for filters, etc. I might end up deleting a lot of these later since there's so many and it's hard to maintain them in a quality way.

gen
---
abstractions for generating sound

* `analog~` - analog simulation. basically supposed to be like line noise and a small dc offset. probably not a very good simulation of the actual analog sound.

* `noisef~` - noise frequency

* `playsf~` - play a file from the argument.

* `pm~` - phase modulation oscillator, stolen from PDX7, with a slight modification.

* `psndm~` - polyphonic sound player. you can send it midi numbers to play the sample at that value. it has 8 voices.

* `psndp~` - polyphonic sound player. similar to `sndp~` but with 6 voices.

* `pulse~` - non-band-limited pulse wave with modulatable pulse width.

* `rec~` - record a snippet of sound to a table.

* `recp~` - play the a snippet of sound from `rec~`.

* `recsnd~` - allows access to the sound recorded with `rec~` in a similar manner to the way `snd~` allows.

* `saw~` - bipolar version of `phasor~`

* `sine~` - extremely simple sine wave oscillator based on `phasor~` and `cos~`. might change this in the future.

* `sndcf~` - generates a signal to control `snd~` based on frequency of the sound.

* `sndcl~` - generates a signal to control `snd~` based on a `line~` (i.e. with start and end-points and a rate)

* `sndcm~` - generates a signal to control `snd~` based on midi numbers (60 being the default base note)

* `sndd~` - sound duplicate. like `snd~` but does not re-load the file; simply re-uses the table containing the already-loaded file.

* `sndf~` - sound frequency. play a sound at a rate multiplied by the normal rate.

* `sndl~` - sound line. play a sound or snippets of it based a `line~`.

* `sndm~` - sound midi. play a sound based on midi note numbers, with 60 being the default base note.

* `snd~` - sound file. load a sound into a table and read through it via the audio inlet, with 0 being the beginning and 1 being the end.

* `sndp~` - sound play. load a sound into a table and bang to play the whole sound. good for drums.

* `stsnd~` - FIX

* `timestretch~` - "timestretch" a sound by repeatedly going back and forth through it.

* `tri~` - non-band-limited triangle or saw wave.

guis
----
abstractions whose primary purpose is to display information.

* `cpuload` - shows current CPU load average (FIX for pd 0.48)

* `cview` - `ctlin` gui (works as drop-in replacement!)

* `ifiddle~` - `fiddle~` gui (works as a drop-in replacement!)

* `lview` - list view. shows the whole list received and its length.

* `nview` - `notein` gui (works as a drop-in replacement!)

* `scroll~` - scrolling amplitude view.

* `siga~` - signal analysis. shows the current value, average value, maximum and minimum values, and a `vsl` to plot the input. there is also a `bng` to reset the recorded maximum and minimum.

* `spectrum~` - shows the FFT spectrum of the input.

* `tview` - text viewer. scrolls the last 5 received inputs.

* `view~` - waveform view.

* `vsig~` - "view signal". shows a graphical representation of the signal from -1 to 1.

math
----
abstractions for altering or generating number streams

* `atc~` - "audio to control" - converts a bipolar signal (-1 to 1) to a unipolar signal (0 to 1)

* `atc` - "audio to control" - converts bipolar numbers (-1 to 1) to unipolar numbers (0 to 1)

* `atr~` - "audio to range" - converts a bipolar signal (-1 to 1) to an arbitrary range specified as arguments or via inlets.

* `atr` - "audio to range" - converts bipolar numbers (-1 to 1) to an arbitrary range specified as arguments or via inlets.

* `cta~` - "control to audio" - converts a unipolar signal (0 to 1) to a bipolar signal (-1 to 1)

* `cta` - "control to audio" - converts unipolar numbers (0 to 1) to bipolar numbers (-1 to 1)

* `ctr~` - "control to range" - converts a unipolar signal (0 to 1) to an arbitrary range specified as arguments or via inlets.

* `kinv~` - signal inverter. 0 becomes 1, 1 becomes 0, and everything in between.

* `kinv` - number inverter. 0 becomes 1, 1 becomes 0, and everything in between.

* `maybe` - maybe output a bang. numbers between 0 and 1 specify a probability of a bang (i.e. 0.25 is 25% chance of bang), numbers above 1 specify 1 in n chance of bang (i.e. 5 is 1 in 5 chance of bang, or 20%). banging the inlet is a 50% chance of bang.

* `minv` - "midi invert". 127 becomes 0, 0 becomes 127, and everything in between.

* `mrange` - scale 0-127 to an arbitrary range.

* `num` - holds a number and allows you to add, subtract, multiply, or divide from that number via messages.

* `rangem` - scale a range to midi (0-127).

* `reciprocal` - outputs the reciprocal of the input.

* `round` - round a float to the nearest integer.

* `rrange` - random within a range (inclusive).

* `rtr` - "range to range" - scale one arbitrary range to another arbitrary range.

* `transposer` - outputs number to multiply a frequency by in order to shift it by a number of semitones (provided as input or argument)

seq
---
sequencer abstractions

* `adsr~` - attack decay sustain release envelope... well, kinda.

* `adsr` - same as `adsr~`, but outputs messages instead of audio signal.

* `aline~` - automatic line. like `line~` but floats don't jump, they start a line whose time is provided by the first argument.

* `aline` - automatic line. like `line` but floats don't jump, they start a line whose time is provided by the first argument.

* `amap` - advanced version of `map`. has more features like random selection, insertion, deletion, and dumping the contents.

* `anaseq` - a sequencer made of vertical sliders; supports saving, loading, multiple patterns and more.

* `beat~` - make beats from a phasor by dividing the phasor into $1 sections and outputting a bang every $2 sections.

* `boxseq` - 6x6 "box" sequencer. can be played in any direction, even diagonally. was an experiment. might change it later.

* `bpma` - "bpm any". WIP.

* `bpmm2` - was supposed to be the next version of `bpmm` with fewer outlets but I might delete this actually.

* `bpmm` - metro/gui for outputting bangs on the downbeat, bangs on each quarter note, and numbers for each quarter note. try connecting the third outlet to `anaseq` or `drumseq`

* `drumseq` - a 16x4 matrix of toggle boxes. supports saving, loading, multiple patterns and more.

* `dust` - output bangs at random intervals lower than the provided argument.

* `edger~` - basically a convenient interface to `edge~`. left outlet bangs on a zero to non-zero transition, while the right bangs on a non-zero to zero transition.

* `ft` - "friendly table". abstraction to make it easier to edit a table. need to redo this.

* `hash` - hash table. operates similarly to `table` except keys and values can be any symbol, rather than just integers. see also: `hashread`, `hashwrite`

* `hashread` - read from `hash`'s hash table. analogous to `table`'s `tabread`.

* `hashwrite` - write to `hash`'s hash table. analogous to `table`'s `tabwrite`.

* `iadsr~` - interface ADSR envelope. WIP.

* `ilist` - indexed list manager. insert into or remove from a list by index, just by sending messages.

* `listman` - list manager. you can add elements to a list, remove them, check for their existence within the list, etc. you can't remove by index, only by value, so don't use this if you want to have multiple of the same element.

* `lmap` - line map. was supposed to be used to generate a complex line. but I might delete this.

* `map` - map bangs or floats to elements of a list provided as arguments or set via the right inlet. probably the most useful abstraction you'll ever find.

* `ometro` - "on metro". a `metro` that is on by default.

* `pattseq` - graphical sequencer similar to `drumseq` but outputs numbers rather than just bangs.

* `pb` - processor for betablocker. basically a little computer.

* `pmap` - program map. related to `pb`.

* `proll` - piano roll-like sequencer. WIP.

* `queue` - a first-in-first-out queue. you can enqueue things onto the queue or dequeue them from it. see also: `stack`.

* `rchoice` - random choice from either the arguments, or from the incoming list.

* `rmap` - receive map. takes as arguments a list of names to receive from, and outputs data received from them with numbers prepended.

* `sbox` - box abstraction used by `boxseq` and `pattseq`.

* `seqfill` - abstraction used by `drumseq`'s "e" command. might remove this in the future.

* `srush` - "snare rush" abstraction. might redo this to make it simpler.

* `stack` - a last-in-first-out stack. you can push things onto the stack or pop them off of it. see also: `queue`.

* `taptempo` - tap or send bangs to get the tempo.

* `td~` - table draw. supposed to draw into a table via messages, but it's not finished yet. probably never will be. might delete this.

* `tmap` - timed map that plays through the whole list with one bang.

* `tracker` - simple "tracker" sequencer controllable via the keyboard.

* `unmap` - get the index of incoming values in a list provided either as arguments or via the right inlet. the opposite of `map`. 

* `vslz` - extremely simple 8-step vsl-based sequencer.

synths
------
"full-featured" synthesizers. a lot of these are scrapped designs. most of these aren't that great.

* `hoover~` - hoover synth. WIP.

* `kick1~` - extremely basic kick drum synth

* `kick2~` - another extremely basic kick drum synth

* `kick3~` - yet another extremely basic kick drum synth

* `snare1~` - extremely basic snare drum synth

* `snare2~` - another extremely basic snare drum synth

* `tb303~` - TB303 clone. probably doesn't sound much like the real thing. WIP

utils
-----
miscellaneous utilities

* `*+~` - multiply and then add to a signal with one object.

* `autosend` - use the first item in a message as the destination for the rest of the message.

* `chars` - separate a symbol into a list of its characters.

* `colors` - outputs a pd color when the left inlet is banged. otherwise, the inlets take floats: from left, the red amount, green amount, and blue amount.

* `e` - "every". only pass every $1 inputs, with an offset of $2.

* `emptysymbol` - test if a symbol is the empty symbol.

* `hue_to_rgb` - convert a hue to rgb colors. see also: `colors`

* `interval` - outputs time between bangs, measured with `realtime`.

* `itimer` - interface timer. shows minutes, seconds, and milliseconds.

* `ktimer` - timer abstraction. outputs minutes, seconds, and milliseconds from an internal `realtime` object. this is used by `itimer` but I might delete this.

* `lb` - `loadbang` abstraction. lets you output a specific number or value on load, rather than just a bang.

* `limit~` - handy limiter abstraction. basically just outputs a signal limited by `limiter~` in case you're lazy like me. be warned that this introduces a delay of 64 samples, of course.

* `list-find-1` - basically the same as `list-find` but only finds the first instance of an item in the list.

* `list-replacer` - replaces all instances of one item in a list with another list.

* `lists` - list store. basically works how `float` and `symbol` work, except, of course, that it's for lists.

* `list-without` - returns a list without all instances of the specified element.

* `marquee` - display elements of a list at regular intervals.

* `mp3conv` - use the `lame` command-line utility to convert an mp3 to wav, storing the wav in /tmp and outputting the filename of the wav when conversion finishes. obviously you'll need to have `lame` installed in order for this to actually work.

* `o~` - interface for mono output to `dac~`.

* `parser` - parses lisp-style commands from within the incoming message (i.e. "(function argument1 argument2 ... argumentN)") and outputs the original message with the output of each command replacing the command. currently accepts "rc" for `rchoice` and "rr" for `rrange`. it's a decent start but I will probably add memory to it as well. maybe eventually it will be a full-fledged lisp implementation! ha.

* `po~` - panned mono output. same as `o~` but the first argument is the stereo panning position of the input, from -45 to 45.

* `porta~` - portamento. might need work.

* `qtabwrite` - quick tab write. specify a table as the argument, and then you can send messages to the inlet or to qt-$1 in the format "INDEX VALUE"

* `qtimer` - quantizible timer. similar to `interval` but allows you to specify the granularity of output values.

* `quote` - surrounds the input with quotes.

* `rporta~` - relative portamento. might need work.

* `so~` - interface for stereo output to `dac~`. see also: `o~`.

* `spacesym` - outputs a symbol that has a character that looks blank. thus, you can make symbols with "spaces" in them without them being lists. it's one of pd's quirks. don't know if this'll work everywhere.

* `span~` - simple panner. like `pan~` but lets you specify the panning position as an argument if you're lazy.

* `sreceive~` - settable receive. probably don't use this.

* `ssend~` - settable send. probably don't use this.

* `sym` - turn a list into a symbol (basically just `l2s` with an empty symbol sent to the right inlet. see also: `chars`)

Future
======

In the future I plan to clean up a lot of these. Either by renaming them or by splitting up functionality, etc. There are also a few that i'd like to re-code or rethink entirely. Some of the things I want to change:

* make sure all of these abstractions work with the new version of Pd (vanilla).
* sort through these folders: ctrl, demos, examples, fx, math, seq, utils
* clean out this library - remove incomplete extensions
* split out the LADSPA abstractions into their own library.
* rename `adsr` and `adsr~` to just `adr` and `adr~` and remove the sustain functionality
* remake `adsr` and `adsr~` into actual ADSR envelopes
* `atc`, `cta`, `atr`, and the others should probably be renamed to something like `btu`, `utb`, and `btr`, since the technical term for a signal from 0 to 1 is "unipolar" and the technical term for a signal from -1 to 1 is "bipolar"
* see if there are better ways to analyze the "volume" of a sound for `scroll~`
* re-add `mc` for `o~`??
* make a better `analog~`
* remove `seqfill` maybe.
* redo `ft` maybe.
* implement voice stealing in `polys`
* get `tracker` to use `kfilename`
* make `randomsong~` use `mp3conv` and fix `mp3conv`
* finish `proll`
* add keyboard shortcuts to `drumseq` and other "bigger" abstractions.
* update `snd~` so that you can also index the sound by samples if the index is above 1.
* finish `looper~`
* replace `drumseq` with the new `drumseq2`
* finish `grain~` and `granular~`
* remove a lot of the stuff in "fx", since a lot of it either sucks or isn't even original material.
* make an "examples" folder full of better examples instead of cramming as many abstractions as possible into crappy "demos"
* rename `scroll~` to something more descriptive
* finish `tb303~` (add accent function, perhaps improve GUI further) and `hoover~`
* finish writing help files for all abstractions

Here are some things i'd like to be able to do, but can't (due to either bugs/missing features in Pure Data, or just my lack of knowledge):

* make `keyonchg`, `keyonoff`, etc work properly (pd's `keyname`, `key`, `keyup`, etc, all detect from keyboard "repeat" events rather than actual physical keypresses or releases)
  * actually, this is probably because i'm using X, and X sucks. can't wait for wayland!
* remove `span~` (pd's `pan~` object would need to accept an argument for this to happen)
* make `kfilename` (and all abstractions that use it) able to handle filenames with spaces (should be possible in pd 0.44)

Here are a few ideas I have:

* make a bunch of abstractions for "patterns" based off of SuperCollider's pattern library.
* make `cline` (controllable line using `mc` and keyboard shortcuts or messages)
  * make `o~` and the like use `cline` for the volume controls
