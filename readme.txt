This is a quick script to generate 3D spatialized sounds for playback using jsonic (http://mindtrove.info/jsonic-speech-and-sound-using-html5/). 

I'm using the HRTF (head-related transfer function) measurements of a KEMAR dummy head micrphone data from MIT. The script should work on any sound format that sox can read. Run it like:

python hrtf.py infile outfolder

It will create the folder if it doesn't already exist. In the outfolder it will create files with names like a40.ogg which is the sound at 40 degrees azimuth with 0 degrees elevation. We could do elevation too but I stuck with only the horizontal plane for this.

It works by using sox to recode whatever format you give it to 22050Hz, mono, 16 bits. Then, for azimuth steps of 5 degrees it applies the HRTF filters to produce the left and right channels, and writes a wav file out. Then it uses sox again to encode the wav file to ogg and mp3 formats.

You'll need python + numpy + scipy + sox to use this.
