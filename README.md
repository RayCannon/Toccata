# Toccata
Toccata from J.S.Bach "Toccata and Fugue in Dm" written in APL

Initially based on the code from  WAVE, this APL workspace produces a ".WAV" sound file with a rendition of J.S.Bach famous Toccata.
The file Music.wav is 35Mb in size and plays for 1 minute, 33 seconds.

The code (Music.dws) is all written in Dyalog APL W Version: 18.2.45405.0 64 Unicode and writes the "MUSIC.WAV" file to disc.

All the sound is genorated from sine waves for the funemental notes with added harmonics in an attempt to sysnthise the sound of organ pipes.  

To play the "MUSIC.WAV" file  from APL, a ⎕NA call to MS "PlaySound" from Winmm.dll, is made.
The disc file produced can also be played by MS Media Player and many other apps.

My primary sorce for the music was score arranged for piano solo by Thomas A. Johnson (which I bought back in 1972), but I also used various YouTube videos.

All the code is contained in the root namespace, but at runtime, a namespace call G (for Globals) is created to contain many global variables, mainly related to musical terms.
Within namespace G are items such as:
  Musical loudness EG fff, ff, f, mf,  mp, p, pp and ppp; 
  Musical note length EG W(hole), H(alf), Q(uarter), E(ighth)......(also dotted notes and triplets)
  Musical tempos EG Grave, Lento, Largo, Adgio,.......
  and named musical note frequencies, from C0 (16.3725Hz) up to B5 (982.35Hz)
  
The "transcription" from standard musical notation involves having a set of vectors for each note or cord.
The full set has a frequency value for each note/cord, a note length, a tempo and a loudness. 
In addition, the current selected  "pipe" defines the harmonics and their relative decibel levels to be applied to the fundemental notes.

An earlier Git repositry of mine (WAVE) attempting the same proess, suffered from "pops and crackels" due to discontinuties as notes changed.
This implementation dose not suffer from this problem, due to the use of multiple overlapping "voices", so one note never cuts off another.


  
