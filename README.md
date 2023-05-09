# Toccata
The Toccata from J.S.Bach "Toccata and Fugue in Dm" written in APL

Initially based on the code from  WAVE, this APL workspace produces a ".WAV" sound file with a rendition of J.S.Bach famous Toccata.
The file Music.wav is 35Mb in size and plays for 1 minute, 33 seconds. 
Note: You may wish to convert the large WAV file into a much smaller MP3 file for convenience. Many free apps are available.

The code (Music.dws) is all written in Dyalog APL W Version: 18.2.45405.0 64 Unicode and writes the file "Toccata.WAV" to disc.
(The full file and path name may be altered in the main function "WriteMusic".)

All the sounds are genorated from sine waves, first for the fundamental notes, and harmonics are added, in an attempt to synthesise the sound of organ pipes.  

To play the "Toccata.WAV" file  from APL, a ⎕NA call to MS "PlaySound" (from Winmm.dll), is made.
The disc file produced can also be played by MS Media Player and many other sound apps.

My primary source for the music was score arranged for piano solo by Thomas A. Johnson (my copy is from 1972), but I also used various YouTube videos.

All the code is contained in the root namespace, but at runtime, a namespace call G (for Global) is created to contain many global variables, mainly related to musical terms.
Within namespace G are items such as:
  Musical loudness EG fff, ff, f, mf,  mp, p, pp and ppp; 
  Musical note length EG W(hole), H(alf), Q(uarter), E(ighth)......(also dotted notes and triplets)
  Musical tempos EG Grave, Lento, Largo, Adgio,.......
  and named musical note frequencies, from C0 (16.3725Hz) thru A4 (440Hz) up to B5 (982.35Hz)
  
The "transcription" from standard musical notation involves having a set of vectors for each note or cord.
The full set has a frequency value for each note/cord, a note length, a tempo and a loudness. 
In addition, the current selected  "pipe" defines the harmonics and their relative decibel levels to be applied to the fundamental notes.

An earlier Git repository of mine (WAVE) attempting the same proess, suffered from "pops and crackles" due to discontinuities as notes changed.
This implementation dose not suffer from this problem, due to the use of multiple overlapping "voices", so one note never cuts off another.

Within the function MakeMusic is the function Play_Toccata which splits the music into smaller parts for ease of editing. 
It also contains an function "TestPipes" to test out the sounds of the different "organ pipes" with their varying harmonics.
The source of my knowledge here is based on "Observations on organ pipe sounds" a web page by Colin Pykett.
http://www.colinpykett.org.uk/observations-on-organ-pipe-sounds-frequency-spectra.htm#Introduction
but I have greatly simplified the information from Colin's work.

The current settings of the selected pipes has no real reasoning behind it, much of it being me just playing around. At best it just "sounds" more interesting
than the simple sine wave I originally used. In the same way I have played with the mono/stereo settings.




  
