# Audio & Video #

## Splitting Mp3 ##

Install via

	sudo port install mp3splt

Usage:

	mp3splt -c music.cue music.mp3
	
Which pumps out the named files into the same directory

## Extracting audio track ##

### From AVI Container ###

Install via

	sudo port install ffmpeg

Usage:

	ffmpeg -i file.avi -f mp3 file.mp3

### From Matroska Video (MKV) files ###

Install via

	sudo port install mkvtoolnix
	
Which took ages (2+ hours, mainly because of Boost).

List contents of mkv file

	mkvmerge -i file.mkv
	
Output will be something like:

	File 'file.mkv': container: Matroska
	Track ID 1: subtitles (S_TEXT/ASS)
	Track ID 2: audio (A_MPEG/L3)
	Track ID 3: video (V_MPEG4/ISO/AVC)
	
Extract tracks with `mkvextract`

	mkvextract tracks MovieFile.mkv 1:thesubtitles.srt 2:theaudio.mp3 3:thevideo.mp4
	
Or just the audio track

	mkvextract tracks MovieFile.mkv 2:theaudio.mp3 