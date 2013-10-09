drumtranscription_max-for-live
==============================================================

**An open-source streaming drum transcription system for MaxMSP/MaxForLive**

We implemented an audio drum transcription algorithm in MaxMSP, which can transcribe kick, snare, and hi-hat from live drum performances. The software takes live audio or files as input and triggers events for each drum type as output.

This repository contains a MaxForLive implementation of the application in MaxMSP repository, as well a MaxMSP abstraction of the device.
This device works in Ableton Live environment as a 'audio effect' device,
and receives as input a live audio signal from external source (microphone) or from audio files. It generates MIDI notes for every detected kick, snare or hihat sound.
The MIDI data can be dumped to MIDI clips in Ableton's session view, or feed to another track(through a receiver device) for further processing, ie. to trigger effects, sounds or instruments.
Check the accompanying pdf manual for more info. 

The MaxMSP patches and the source code for some of the MaxMSP externals are distributed under GPLv3 license - Copyright 2012-2013 - INESC-Porto.


----------------------------
##Installation / Quick Start

**There are two apps available for the user. One MaxForLive device to be used in Ableton Live and the MaxMSP counterpart to be used in Cycling 74 MaxMSP.**


####LiveDrumTranscription_M4L.amxd

This is a frozen version of the device. It contains all necessary externals and patches. 
It can be dropped directly into a audio track in Ableton Live and used right away.
In order for the device to work properly the user must keep the folder "database_fast" ALWAYS in the same folder of the device.


####LiveDrumTranscription_MAX.maxpat

This is the MaxMSP counterpart of the M4L device.
This app works as a bpatcher abstraction.
To test it open the help file inside 'patchers' folder or use the alias here (LiveDrumTranscription_MAX.maxhelp alias).
 
MaxMSP must know where to look in your hard-drive for the necessary externals and patches.
It can be used either in two ways:
- First
 + Add the patchers folder to MaxMSP search path (file preferences). This folder contains all necessary abstractions and externals;
 + Add a bpatcher to your patch, open inspector and type in "patcher file" parameter LiveDrumTranscription_MAX.maxpat;

- Second
 + Or, work always with the abstraction (LiveDrumTranscription_MAX.maxpat) inside the patchers folder.

***ATTENTION!!!
Keep the database folder always together with the abstraction and the M4L device!***


In order to use this application, you will need to have the visual programming environment MaxMSP installed. The software can be used for free for a period of 30 days. We recommend using the latest version.

----------------------------
##WHO CAN USE THIS SOFTWARE?

This software can be used by musicians, visual artists, and researchers. Musicians can control their music performance using the live transcription from the drums. Artists can generate visuals based on the drum events. Scientists can reproduce and compare any part of the research. Furthermore, they can use this system in designing better systems for machine listening or music interaction.

Some MaxMSP knowledge is required if you plan to make serious modifications to the patches.

----------------------------
##TROUBLESHOOTING

The error messages are displayed in the MaxMSP window. The most common errors are related to external patches missing, or using a very old version of MaxMSP.

If you receive the "not found" error in the message window, then make sure that you are using the version which corresponds to your operating system, and that you are using the latest version of MaxMSP.

----------------------------
##DETAILED DESCRIPTION

The research behind this system is documented in an ICASSP 2013 paper:
http://www.icassp2013.com/Papers/ViewPapers.asp?PaperNum=4116

The algorithm comprises three different stages: onset detection, feature computation and classification. We implemented patches several versions for each of the stages.
- onset detection - you can use a faster onset detector or the slower one with better resolution
- you can use the faster feature computation which takes just the first 56 ms, or you can use the "best" patch which overlaps 10 frames summing 136 ms of analysis
- you can choose between a trained KNN classifier or a sequential K-means classifier


In the MaxMSP and PureData repositories you can find the C source code for the externals inside the src directory.

The overlapping sounds database can be downloaded from: 
http://www.mediafire.com/download.php?q8nl199bnz7g68n
OR
https://www.dropbox.com/s/6ykurx3lr9s0lj5/overlapping_sounds_db.zip

*This work is supported by the ERDF – European Regional Development Fund through the COMPETE Programme (operational programme for competitiveness) and by National Funds through the FCT – Fundacao para a Ciencia e a Tecnologia (Portuguese Foundation for Science and Technology) within project Shake-it, Grant PTDC/EAT-MMU/ 112255/2009. Part of this research was supported by the CASA project with reference PTDC/EIA-CCO/111050/2009 (FCT), and by the MAT project funded by ON.2.*

----------------------------
##FUTURE WORK

We plan to implement an external which will take a buffer of audio samples and will separate the sound in two streams: harmonic and percussive. In this way, we can transcribe drums from polyphonic audio, and not only from audio comprising solely drum sounds. 

----------------------------
##HELP

Please contact miron.marius[at]gmail[dot]com or dcocharro[at]gmail[dot]com, for further questions. 