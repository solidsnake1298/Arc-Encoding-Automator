# Arc-Encoding-Automator
Automates media encoding to AV1, including handling language selection, converting Dolby Vision to HDR10, and converting Dolby/DTS audio to OPUS.

# Requirements
- Linux kernel 6.2+.
- ffmpeg, but tested with Jellyfin-ffmpeg 6.0.1, 7.0.2, and 7.1.1 symlinked to /usr/bin.
- Intel GPU with AV1 encoding support.
- Dolby Vision removal functionality requires Jellyfin-ffmpeg 7.0.2-4 and newer.
- jq - Available in most package repos.
- bc - Available in most package repos.

# Options
- -i Input file (required)
- -c Number of chapters per episode when splitting monolithic TV show files.
- -s Provide list of colon separate chapter numbers per episode, episodes separated by commas.  This covers instances where some episodes have an extra chapter for one or more episodes. An example where the first episode has 6 chapters, while the rest of the file has 5 chapters.
  - -s "00:05,06:10,11:15,16:20,21:25,26:30,31:35,36:40,41:45,46:50,51:55,56:60,61:65,66:70"
- -a For use with Anime and other Japanese content.  Modifies language selection to also select Japanese in addition to English audio/subtitle tracks.
- -k For use with Korean content.  Modifies language selection to also select Korean in addition to English audio/subtitle tracks.
- -m For use with Chinese/HK content.  Modifies language selection to also select Chinese in addition to English audio/subtitle tracks.
- -h Disables hardware decoding for codecs Arc GPUs don't support decoding.  Only needed for edge cases I haven't encountered yet.  Common codecs Arc doesn't support decoding already disable hardware decoding automatically.  The following source codecs will automatically disable hardware decoding: MPEG1, MPEG4, XVID, VC1, VP8, H264 Hi10p, H264 422, H264 444, and WMV codecs.
- -w Provide path for scratch directory.  Ideally, this should be on a separate disk from the input file to reduce disk I/O and improve throughput for the remux step.  Use quotes or escapes if path contains spaces or special characters.
- -e Language selection only.
- -o Encodes audio, passes thru video, selects audio/subtitle tracks.
- -t Forces de-telecine when telecine detection does not conclusively return a result.  1) 24fps/48fps in 30fps/60fps mode  2) 24fps in 60fps mode  3) Progressive in interlaced mode

