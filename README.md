# Toccata
The Toccata from J.S.Bach "Toccata and Fugue in Dm" written in APL

This code is a replacement for my WAVE repositiary.

This APL workspace produces "TOCCATA.WAV" (a sound file) with a rendition of J.S.Bach famous Toccata and writes it to disc.
The file Toccata.wav is 35Mb in size and plays for 1 minute, 33 seconds. 
Note: You may wish to convert the large WAV file into a much smaller MP3 file for convenience. Many free apps are available such as https://cloudconvert.com/.
I have included the "Toccata.mp3" file because "Toccata.wav" was way too big to upload into Github.

Almost all the code in Music1.dws is written in Dyalog APL/W-64 Version: 18.2.45405.0 64 Unicode and it saves the file "Toccata.WAV" to disc.
(The full file and path name may be altered in the main function "WriteMusic", by default it is written to the same directory as the workspace.) 

To play "Toccata.WAV" from APL, a ⎕NA call to MS "PlaySound" (from Winmm.dll), is used. It can also be played by MS Media Player and many other sound apps.
The other non-APL call is made via ⎕NA from the function ExpandPath, using "GetFullPathName" from kernel32.DLL.

My primary source for the music was score arranged for piano solo by Thomas A. Johnson but I also used various YouTube videos.

All the sounds are genorated from sine waves, first for the fundamental notes, and harmonics are added, in an attempt to synthesise the sound of organ pipes.  

All the code is contained in the root namespace, but at runtime, a namespace called G (for Global) exists to contain many global variables, mainly related to musical terms.
Within namespace G are items such as:
  Musical loudness EG fff, ff, f, mf,  mp, p, pp and ppp; 
  Musical note length EG W(hole), H(alf), Q(uarter), E(ighth)......(also dotted notes and triplets)
  Musical tempos EG Grave, Lento, Largo, Adgio,.......
  and named musical note frequencies, from C0 (16.3725Hz) thru A4 (440Hz) up to B5 (982.35Hz)
  
The "transcription" from standard musical notation involves having a set of vectors for each note or cord to be played.
The full set has a frequency value for each note/cord, a note length, a tempo and a loudness. 
In addition, the current selected  "pipe" defines the harmonics and their relative decibel levels to be applied to the fundamental notes.

The earlier Git repository of mine (WAVE), attempting the same proess, suffered from "pops and crackles" due to discontinuities as notes changed mid phase.
This implementation dose not suffer from this problem, due to the use of multiple overlapping "voices", so one note never cuts off another.

Within the function MakeMusic is the function Play_Toccata which splits the music into smaller parts for ease of editing. 

It also contains a function "TestPipes" to test out the sounds of the different "organ pipes" with their varying harmonics.
The source of my knowledge here was gained by reading "Observations on organ pipe sounds" a web page by Colin Pykett.
http://www.colinpykett.org.uk/observations-on-organ-pipe-sounds-frequency-spectra.htm#Introduction

In this version, I have added some reverberation (via a function called Echo), that attempts to add the effect of a hall with a 60db loss after 2 seconds.
Other room "ambiences" may be created by playing with setting within the function "Echo".

The current settings of the selected pipes has no real reasoning behind it, much of it being me just playing around. At best it just "sounds" more interesting
than the simple sine wave I originally used. In the same way I have played with the mono/stereo settings.

The function "Avoice" returns the sample values need to produce a simple sine wave with the requested frequency and length, which in term depends on the tempo.

The function "Crescendo", has been used to procude Crescendo, but may also produce a Decrescendo. 

The function "BuildPart" deals with smaller parts of the music to prevent WS FULL when dealing with cords and multiple voices and also the harmonics of the selected organ "pipe", while keeping all the voices synchronized.

The function "Stereo" deals with the absolute volome of the overall piece and "merges" the left and right hand channels as required by a WAV file.
I have concidered having more than 2 channels (up to 65535 could be supported) but that would vastly increase the size.
  
A final note on "loudness", which is non-linear. See function "Initialise" for the decibel values I have used for the musical loudness levels.
