= = = = = = = = = = = = = = = = = = = = = = = = = = = = = = 
	LVDAU: Low Volume Detection - Audio Utility
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

	Build command-line arguments for Visual C++ on Windows
	
		Compilation:
			
			/EHsc
			/FS
			/std:c++14
			"/D"_USING_V110_SDK71_
			"/D"WIN32
			"/D"_WIN32
			"/D"WIN64
			"/D"_WIN64
			"/D"MBCS
			/O2
			/W4
		
		Linking:
	
			/OPT:REF


	USAGE
-----------------

		-ifn <FILE>
			Input file for processing.
			The only supported file format is WAVE (.wav).
			The only supported sample formats within the WAVE file are:
				* PCM 16-bit signed integer (pcm_s16le)
				* PCM 8-bit unsigned integer (pcm_u8)
			To read from the standard input (STDIN) set it to "-"

		-ofn <FILE>
			Output file for processed audio data.
			The only possible output format is WAVE (.wav).
			The only possible sample format is pcm_s16le, mono.
			To write to the standard output (STDOUT) set it to "-"

		-silence_threshold <VALUE>
			Silence detetection parameter, threshold.
			The lower value, the lower volume will be considered
			as the silence. Value must be between 0.0 and 1.0.
			Typical "silences" should be below 0.2.
			Default: 0.200000

		-min_silence_duration <SECONDS>
			Silence detetection parameter, minimum duration.
			How many time of the silence there must be to
			consider it for processing, f.e. removal.
			Default: 0.250000 seconds

		-shrink_to <VALUE>
			Fraction value in the range from 0.0 to 1.0 to shrink,
			time compress, every detected silence to.
			For example, 0.5 shrinks the silence to 50 percent.

		-probe_duration <SECONDS>
			Advanced. Silence detetection parameter, probe duration.
			It is recommended to leave the default.
			Specific to the method used by the code.
			Value in seconds of how many audio samples to use to
			determine if the audio is silent.
			Default: 0.005000 seconds

		-loglevel <VALUE>
			Set log-level of the program.
			Possible values: error, warning or debug.
			Can be set to a numerical value 0 to suppress most of
			the messages.

		-fshow_params
			If present, shows the summary of program configuration.
			Use -fshow_params_only instead to exit afterwards.

		-finfo_only
			If present, shows file information only, then exits.

		-fshow_build_info
		-main_buffer_size <NUM_BYTES>
		-fno_unit_tests
		-fignore_leading_silence
		-fignore_middle_silences
		-fignore_trailing_silence

		-fupdate_stdout
			Workaround when writting the data to STDOUT and the data is not preocessed.
			Forces update of the Wave header, at the finalization step, as-if
			the stream was a disk file. Valid only in STDOUT mode. Shouldn't be used
			normally, when passing the data via the pipe.
			May cause noticeable corruption at the end of the audio stream.

		-silence_log_file <FILE>
			Additional output text file that will have all detected silences.
			Format used is Ffmpeg's ffconcat.

		-silence_ref_file <NAME>
			For use with '-silence_log_file'. Specify file name that
			is inserted inside the log file. Otherwise used is that from '-ifn'.

		-help
			Shows this help message.

