# lvdau
Detects and removes silence from audio streams or files.
command line utility for Windows and Linux platforms.
Can be configured to read and/or write audio data to/from 
standard strems (STDIN, STDOUT) making it compatible with other 
command line tools and process any type of audio.

detected silence can be time compressed (shrinked) or removed.
main configuration options can specify volume threshold, minimum duration and time compression factor.

by default, silence is removed from anywhere in the stream,
but can be changed to leave silence in the middle and
renove only leading or trailing parts.

Internally, the only recognized audio format is Wave-PCM.

  
