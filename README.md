# Toccata
From J.S.Bach Toccata and Fugue in Dm written in APL

Initially based on the code from  WAVE, this code produces a ".WAV" sound file with a rendition of J.S.Bach famous Toccata.

All the sound is genorated from sine waves for the funemental notes with added harmonics to attempt to sysnthise organ pipes.  

The code is all written in Dyalog APL W Version: 18.2.45405.0 64 Unicode and writes the ".WAV" file to disc.

To play the ".WAV" file  from APL, a ⎕NA call to MS "PlaySound" from Winmm.dll, is made.
The disc file produced can also be played by MS Media Player and many other apps.

My primary sorce for the music was score arranged for piano solo by Thomas A. Johnson which I bought in 1972, but I also used various YouTube videos.

