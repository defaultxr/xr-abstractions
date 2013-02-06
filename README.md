defaultxr's pure data abstractions
==================================
This is a collection of pure data abstractions i've made. This repository is now officially the place to find my abstractions.

Please notify me of any bugs you find while using these abstractions.

I'm still working on writing help files for each of these. This collection is under constant development, so things might change, get renamed, removed, etc. But it's fairly likely it won't cause you any problems.

Some of the abstractions i find most useful are: `map`, `snd~` (and all the objects whose name includes "snd"), `o~`, `view~`, `drumseq`, `rrange`, `rchoice`, `bpmm`, `tb303~`, `rmap`, and `unmap`.

Below is a quick overview of the included abstractions.

analysis
========
abstractions for analyzing stuff or displaying information.

`attacks~` - supposed to generate a list of a sound file's 'attacks', which could then be used for `snds~`. WIP.

`cpuload` - display current CPU load average

`cview` - view all incoming midi CC

`ifiddle~` - graphical interface to `fiddle~`.

`lview` - list view. shows the whole list received, as well as its length.

`nview` - view all incoming midi note values.

`scroll~` - scrolling amplitude view.

`siga~` - signal analysis. shows the current value, average value, maximum and minimum values, and a `vsl` to plot the input. there is also a `bng` to reset the recorded maximum and minimum.

`signum~` - current value of the signal. basically like `unsig~` with a number box gui.

`spectrum~` - shows the FFT spectrum of the input.

`tview` - text viewer. scrolls the last 5 received inputs.

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

`c` - midi continuous controller interface

`editmode` - (try to) detect edit mode

`inputd` - input accumulator deluxe

`inputn` - input accumulator for numbers

`input` - input accumulator

`kbdm` - convert numbers from `key` into midi note numbers so you can use your keyboard to play notes.

`keynum` - get numbers from the keyboard. if "h" is provided as the first argument, also allows hexadecimal numbers (a-f).

`keyonchg` - 

`keyonoff` - 

`keyrow` - converts numbers from `key` into the numbers 0-9. in other words, use a row of keys as numbers.

`kfilename` - abstraction for making paths. used by `snd~`, `drumseq`, `anaseq` and others. **NOTE: you might want to edit this since it uses my paths.**

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

`nems` - non-edit mode spigot. only allows messages to pass when edit mode is off. doesn't work though

`nkeyb` - 

`nkey` - 

`nknum` - 

`numlock` - shows whether numlock is on or off and also outputs 1 or 0 depending.

`polys` - similar to pd's built-in `poly` but allows you to specify a specific voice with note-offs (i.e. so you can have multiple voices with the same note). WIP: voice stealing is not yet implemented.

`router` - 

`sndsel` - sound selector. allows you to select a sound by browsing folders graphically, because `playlist` kind of sucks. it's a work-in-progress, but it's probably ready for regular use.

`sswitcher~` - 

`switcher~` - 

`switcher` - 

`wiib` - 

`wiimotec` - 

`wiisring` - 

demos
=====
demonstrations of the included abstractions (definitely open these if you want a tour of this library)

fx
===

abstractions for many LADSPA effects, as well as interfaces for filters, etc.

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

`pm~` - phase modulation oscillator, stolen from PDX7, with a slight modification.

`psndm~` - polyphonic sound player. you can send it midi numbers to play the sample at that value. it has 8 voices.

`psndp~` - polyphonic sound player. similar to `sndp~` but with 6 voices.

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

`maybe` - maybe output a bang. numbers between 0 and 1 specify a probability of a bang (i.e. 0.25 is 25% chance of bang), numbers above 1 specify 1 in n chance of bang (i.e. 5 is 1 in 5 chance of bang, or 20%). banging the inlet is a 50% chance of bang.

`minv` - "midi invert". 127 becomes 0, 0 becomes 127, and everything in between.

`mrange` - scale 0-127 to an arbitrary range.

`num` - holds a number and allows you to add, subtract, multiply, or divide from that number via messages.

`rangem` - scale a range to midi (0-127).

`round` - round a float to the nearest integer.

`rrange` - random within a range (inclusive).

`rtr` - "range to range" - scale one arbitrary range to another arbitrary range.

`transposer` - outputs number to multiply a frequency by in order to shift it by a number of semitones (provided as input or argument)

seq
===
sequencer abstractions

`adsr~` - attack decay sustain release envelope... well, kinda.

`adsr` - same as `adsr~`, but outputs messages instead of audio signal.

`aline~` - automatic line. like `line~` but floats don't jump, they start a line whose time is provided by the first argument.

`aline` - automatic line. like `line` but floats don't jump, they start a line whose time is provided by the first argument.

`amap` - advanced version of `map`. has more features like random selection, insertion, deletion, and dumping the contents.

`anaseq` - a sequencer made of vertical sliders; supports saving, loading, multiple patterns and more.

`beat~` - 

`boxseq` - 6x6 "box" sequencer. can be played in any direction, even diagonally. was an experiment. might change it later.

`bpma` - 

`bpmm2` - was supposed to be the next version of `bpmm` with fewer outlets but i might delete this actually.

`bpmm` - metro/gui for outputting bangs on the downbeat, bangs on each quarter note, and numbers for each quarter note. try connecting the third outlet to `anaseq` or `drumseq`

`drumseq` - a 16x4 matrix of toggle boxes. supports saving, loading, multiple patterns and more.

`dust` - output bangs at random intervals lower than the provided argument.

`edger~` - 

`ft` - "friendly table". abstraction to make it easier to edit a table. need to redo this.

`iadsr~` - interface ADSR envelope. WIP.

`ilist` - indexed list manager. insert into or remove from a list by index, just by sending messages.

`listman` - list manager. you can add elements to a list, remove them, check for their existence within the list, etc. you can't remove by index, only by value, so don't use this if you want to have multiple of the same element.

`lmap` - line map. was supposed to be used to generate a complex line. but i might delete this.

`map` - map bangs or floats to elements of a list provided as arguments or set via the right inlet. probably the most useful abstraction you'll ever find.

`ometro` - "on metro". a `metro` that is on by default.

`pattseq` - graphical sequencer similar to `drumseq` but outputs numbers rather than just bangs.

`pb` - processor for betablocker. basically a little computer.

`pmap` - program map. related to `pb`.

`proll` - piano roll-like sequencer. WIP.

`rchoice` - random choice from either the arguments, or from the incoming list.

`rmap` - receive map. takes as arguments a list of names to receive from, and outputs data received from them with numbers prepended.

`sbox` - box abstraction used by `boxseq` and `pattseq`.

`seqfill` - abstraction used by `drumseq`'s "e" command. might remove this in the future.

`srush` - "snare rush" abstraction. might redo this to make it simpler.

`stack` - a stack. you can push things onto the stack or pop them off of it.

`taptempo` - tap or send bangs to get the tempo.

`td~` - table draw. supposed to draw into a table via messages, but it's not finished yet. probably never will be. might delete this.

`tmap` - timed map that plays through the whole list with one bang.

`tracker` - simple "tracker" sequencer controllable via the keyboard.

`unmap` - get the index of incoming values in a list provided either as arguments or via the right inlet. the opposite of `map`. 

`vslz` - extremely simple 8-step vsl-based sequencer.

`xeroxer~` - 

synths
======
"full-featured" synthesizers. a lot of these are scrapped designs. most of these aren't that great.

`Adder4~` - 

`Adder~` - 

`Adder_voice~` - voice for `Adder~`

`fmFeedback~` - FM feedback synth stolen from NoizeHack, slightly modified by me.

`hoover~` - hoover synth. WIP.

`kick1~` - extremely basic kick drum synth

`kick2~` - another extremely basic kick drum synth

`snare1~` - extremely basic snare drum synth

`snare2~` - another extremely basic snare drum synth

`tb303~` - TB303 clone. probably doesn't sound much like the real thing. WIP

utils
=====
miscellaneous utilities

`*+~` - multiply and then add to a signal with one object.

`autosend` - use the first item in a message as the destination for the rest of the message.

`chars` - separate a symbol into a list of its characters.

`colors` - outputs a pd color when the left inlet is banged. otherwise, the inlets take floats: from left, the red amount, green amount, and blue amount.

`emptysymbol` - test if a symbol is the empty symbol.

`hue_to_rgb` - convert a hue to rgb colors. see also: `colors`

`interval` - outputs time between bangs, measured with `realtime`.

`itimer` - interface timer. shows minutes, seconds, and milliseconds.

`ktimer` - timer abstraction. outputs minutes, seconds, and milliseconds from an internal `realtime` object. this is used by `itimer` but i might delete this.

`lb` - `loadbang` abstraction. lets you output a specific number or value on load, rather than just a bang.

`limit~` - handy limiter abstraction. basically just outputs a signal limited by `limiter~` in case you're lazy like me. be warned that this introduces a delay of 64 samples, of course.

`list-find-1` - basically the same as `list-find` but only finds the first instance of an item in the list.

`list-replacer` - replaces all instances of one item in a list with another list.

`lists` - list store. basically works how `float` and `symbol` work, except, of course, that it's for lists.

`list-without` - returns a list without all instances of the specified element.

`marquee` - display elements of a list at regular intervals.

`mp3conv` - use `lame` to convert an mp3 to wav, storing the wav in /tmp and outputting the filename of the wav when conversion finishes.

`o~` - interface for mono output to `dac~`.

`parser` - parses lisp-style commands from within the incoming message (i.e. "(function argument1 argument2 ... argumentN)") and outputs the original message with the output of each command replacing the command. currently accepts "rc" for `rchoice` and "rr" for `rrange`. it's a decent start but i will probably add memory to it as well. maybe eventually it will be a full-fledged lisp implementation! ha.

`po~` - panned mono output. same as `o~` but the first argument is the stereo panning position of the input, from -45 to 45.

`porta~` - portamento. might need work.

`qtabwrite` - quick tab write. specify a table as the argument, and then you can send messages to the inlet or to qt-$1 in the format "INDEX VALUE"

`qtimer` - quantizible timer. similar to `interval` but allows you to specify the granularity of output values.

`quote` - surrounds the input with quotes.

`rporta~` - relative portamento. might need work.

`so~` - interface for stereo output to `dac~`. see also: `o~`.

`spacesym` - outputs a symbol that has a character that looks blank. thus, you can make symbols with "spaces" in them without them being lists. it's one of pd's quirks. don't know if this'll work everywhere.

`span~` - simple panner. like `pan~` but lets you specify the panning position as an argument if you're lazy.

`sreceive~` - settable receive. probably don't use this.

`ssend~` - settable send. probably don't use this.

`sym` - turn a list into a symbol (basically just `l2s` with an empty symbol sent to the right inlet. see also: `chars`)

FUTURE
======

In the future i plan to clean up a lot of these. Either by renaming them or by splitting up functionality, etc. There are also a few that i'd like to re-code or rethink entirely. Some of the things i want to change:

* rename `kspigot` and `kspigot~` to `ispigot` and `ispigot~`
* rename `adsr` and `adsr~` to just `adr` and `adr~` and remove the sustain functionality
* remake `adsr` and `adsr~` into actual ADSR envelopes
* rename `bswitcher` and the other similar abstractions so that their names are more logical and easy to remember
* `atc`, `cta`, `atr`, and the others should probably be renamed to something like `btu`, `utb`, and `btr`, since the technical term for a signal from 0 to 1 is "unipolar" and the technical term for a signal from -1 to 1 is "bipolar"
* see if there are better ways to analyze the "volume" of a sound for `scroll~`
* fix `mcb`, `mck`, `m-client`, `mcl`, `mc`, `mct`, `mstr`, etc (i've redone these quite a few times already and i still haven't quite gotten them right)
* rename `aphasor~` to `saw~`
* make a better `analog~`
* remove `seqfill` maybe.
* redo `ft` maybe.
* improve `stack` (i.e. add "shift" and "unshift" operations; perhaps make it possible to push non-float elements onto the stack?)
* implement voice stealing in `polys`
* get `tracker` to use `kfilename`
* make `randomsong~` use `mp3conv`
* make `kfilename` (and all abstractions that use it) able to handle filenames with spaces
* finish `proll`
* update `boxseq` and make it 4x4 instead of 6x6.
* add keyboard shortcuts to `drumseq` and other "bigger" abstractions.

Here are some things i'd like to be able to do, but can't (due to either bugs/missing features in Pure Data, or just my lack of knowledge):

* fix `editmode` so that it is accurate 100% of the time (maybe there is a way to query the editmode state of a certain patch - perhaps using `parentdollarzero` and `sys_gui`??)
* make `keyonchg`, `keyonoff`, etc work properly (pd's `keyname`, `key`, `keyup`, etc, all detect from keyboard "repeat" events rather than actual physical keypresses or releases)
* remove `span~` (pd's `pan~` object would need to accept an argument for this to happen)

Help files still need to be written for:

ctrl:
* `cb`
* `c`
* `inputn`
* `input`
* `kbdm`
* `keynum`
* `keyonchg`
* `keyonoff`
* `keyrow`
* `kfilename`
* `khsl`
* `kspigot~`
* `kspigot`
* `mcb`
* `mck`
* `m-client`
* `mcl`
* `mc`
* `mct`
* `mdrums`
* `mono`
* `monos`
* `mspigot`
* `mstr`
* `nems`
* `nkeyb`
* `nkey`
* `nknum`
* `numlock`
* `polys`
* `router`
* `sndsel`
* `sswitcher~`
* `switcher~`
* `switcher`
* `wiib`
* `wiimotec`
* `wiisring`

fx:
* `aliasing~`
* `ampitchshift~`
* `autocap~`
* `autophaser~`
* `bitcrush~`
* `bitflip~`
* `bodeshifter~`
* `cfilter~`
* `chaospad~`
* `chebyshev~`
* `chebys~`
* `chorus~`
* `combsplit~`
* `comp~`
* `cphaser~`
* `crossover~`
* `cvol~`
* `decimator~`
* `declip~`
* `delayorama~`
* `delay~`
* `dist1~`
* `dist2~`
* `divider~`
* `djeq~`
* `djflanger~`
* `dyson~`
* `envdelay~`
* `exp_decay~`
* `expspect~`
* `fad~`
* `fastod~`
* `flange~`
* `flanger~`
* `fmosc~`
* `freqtracker~`
* `gate~`
* `gater~`
* `gband~`
* `gbutthigh~`
* `giantflange~`
* `gl_xover~`
* `gsm~`
* `gverb~`
* `hardgate~`
* `hardlimit~`
* `hermes~`
* `hilbert~`
* `icomb~`
* `idelayorama~`
* `ifilter~`
* `ifv~`
* `imoog~`
* `impulse2~`
* `isvf~`
* `kaoss`
* `karaoke~`
* `lofi~`
* `mcomb~`
* `mfv~`
* `mmf~`
* `multivoicechorus~`
* `phaser~`
* `phaserr~`
* `pingpong~`
* `pitchscalerhq~`
* `pitchscaler~`
* `plate~`
* `pointercast~`
* `rateshift2~`
* `rateshifter~`
* `rateshift~`
* `retroflange~`
* `revdelay~`
* `reverb~`
* `satan~`
* `sc2~`
* `sdly~`
* `shaper~`
* `sidechain~`
* `sifter~`
* `sinus~`
* `skip~`
* `soft~`
* `sqtremolo~`
* `svff~`
* `tap_autopanner~`
* `tap_chorus_flanger~`
* `tap_doubler~`
* `tapedelay~`
* `tap_pink_noise~`
* `tap_reflector~`
* `tap_stereo_echo~`
* `tap_vibrato~`
* `valve~`
* `valverect~`
* `waveshaper~`
* `waveterrain~`

gen:
* `analog~`
* `aphasor~`
* `fluid~`
* `grain~`
* `granular~`
* `irsong~`
* `noisef~`
* `playsf~`
* `pm~`
* `psndm~`
* `psndp~`
* `random~`
* `randomsong~`
* `rec~`
* `recp~`
* `recsnd~`
* `sine~`
* `sndcf~`
* `sndcl~`
* `sndcm~`
* `sndd~`
* `snds~`
* `srec~`
* `timestretch~`

math:
* `atc~`
* `atc`
* `atr~`
* `atr`
* `cta~`
* `cta`
* `ctr~`
* `kinv~`
* `kinv`
* `minv`
* `mrange`
* `num`
* `rangem`
* `rrange`
* `rtr`
* `transposer`

seq:
* `adsr~`
* `adsr`
* `amap`
* `anaseq`
* `beat~`
* `boxseq`
* `bpma`
* `bpmm2`
* `bpmm`
* `dust`
* `edger~`
* `ft`
* `iadsr~`
* `ilist`
* `listman`
* `lmap`
* `ometro`
* `pattseq`
* `pb`
* `pmap`
* `sbox`
* `seqfill`
* `srush`
* `taptempo`
* `td~`
* `tmap`
* `tracker`
* `unmap`
* `vslz`
* `xeroxer~`

synths:
* `Adder4~`
* `Adder~`
* `Adder_voice~`
* `fmFeedback~`
* `kick1~`
* `kick2~`
* `snare1~`
* `snare2~`
* `tb303~`

utils:
* `autosend`
* `browser`
* `chars`
* `hue_to_rgb`
* `itimer`
* `ktimer`
* `limit~`
* `list-find-1`
* `list-replacer`
* `lists`
* `list-without`
* `marquee`
* `mp3conv`
* `o~`
* `parser`
* `*+~`
* `po~`
* `porta~`
* `qtabwrite`
* `qtimer`
* `quote`
* `rporta~`
* `so~`
* `spacesym`
* `span~`
* `sreceive~`
* `ssend~`
