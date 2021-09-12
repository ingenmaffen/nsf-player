# NSF Player

This is a player for NSF-format Nintendo Entertainment System music files. It's written in JavaScript and should work in any major browser.

## Important info

This repository has been forked from [okaybenji](https://github.com/okaybenji/nsf-player). My purpose with this repository is to make it available as a node package so that it can be used easily. I only made small changes to this library so all the appreciation should go to the authors of the original code's creators.


## Changes 

All the changes I've made to the original code base can be found in commit [02687fb](https://github.com/ingenmaffen/nsf-player/commit/02687fbe3301cc3a3a912450653156343955fd57). I replace the octal literals with the parsed counterparts, made `Module` a global variable and exported two functions (`run` and `createNsfPlayer`).
## How to use it (npm version) 

First, install package with 

```shell
npm install nsf-player
```

After that, import it like this

```
import { run, createNsfPlayer } from "../../node_modules/nsf-player/nsf-player.js";
```

and by running the following code snippet, you can use `nsfPlayer`:

```
run(); // this function initiates libgme
const ctx = new AudioContext();
window['ctx'] = ctx; // make ctx a global variable so creatNsfPlayer() can use it
const nsfPlayer = createNsfPlayer(ctx);
nsfPlayer.play('path-to-file.nsf', trackNumber);
```

I used this package in an Electron-based project ([Hello, World!](https://github.com/ingenmaffen/hello-world)), it may not work in a different environment.

## How to use it
Include **libgme.js** and **index.js** in your project.
```
<script src="libgme/libgme.js"></script>
<script src="index.js></script>
```
Create a player by calling `createNsfPlayer`.
```
const nsfPlayer = createNsfPlayer(); // An audio context is created for you.
```
Optionally, you can pass in your own audio context.
```
const ctx = new AudioContext();
const nsfPlayer = createNsfPlayer(ctx);
```
NSF files may contain multiple tracks. Play a track by calling `play` and passing it the path to your NSF file and the index of the track you wish to hear. (Indexes start at 0 and go up.)
```
nsfPlayer.play('./songs/smb.nsf', 2);
```
If you just want to hear the first track, you don't have to pass an index.
```
nsfPlayer.play('./songs/smb.nsf');
```
Stop the music by calling `stop`.
```
nsfPlayer.stop();
```
## Notes
This uses (and includes) libgme, A.K.A. Game_Music_Emu, a library for emulating video game music.
I adapted it from code I found on the web at [onakasuita.org/jsgme](http://onakasuita.org/jsgme/).