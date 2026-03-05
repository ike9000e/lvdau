= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = 
	LVDAU: Low Volume Detection - Audio Utility.
= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = 
	
	Detects and removes silence from audio streams or files.
	Command line utility for Windows and Linux platforms.
	Can be configured to read and/or write audio data to/from 
	standard strems (STDIN, STDOUT) making it compatible with other 
	command line tools and process any type of audio.

	Detected silence can be time compressed (shrinked) or 
	removed. Main configuration options can specify volume threshold, 
	minimum duration and time compression factor.

	By default, silence is removed from anywhere in the stream,
	but can be changed to leave silence in the middle and
	renove only leading or trailing parts.

	Internally, the only recognized audio format is Wave-PCM.
	
	Available are static builds for Debian Linux.
	

	Compilation Overview
---------------------------

	Build command on Linux with GCC:

		$> gcc ./amalg2.cpp -lc -lstdc++ -lm -static -O2 -o lvdau.out

	
