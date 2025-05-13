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
- -a Enable with 1.  For use with Anime and other Japanese content.  Modifies language selection to also select Japanese in addition to English audio/subtitle tracks.
- -k Enable with 1.  For use with Korean content.  Modifies language selection to also select Korean in addition to English audio/subtitle tracks.
- -h Enable with 1.  Disables hardware decoding for codecs Arc GPUs don't support decoding.  Only needed for edge cases I haven't encountered yet.  Common codecs Arc doesn't support decoding already disable hardware decoding automatically.  The following source codecs will automatically disable hardware decoding: MPEG1, MPEG4, XVID, VC1, VP8, H264 Hi10p, H264 422, H264 444, and WMV codecs.
- -w (BETA ONLY) Provide path for scratch directory.  Ideally, this should be on a separate disk from the input file to reduce disk I/O and improve throughput for the remux step.  Use quotes or escapes if path contains spaces or special characters.
- -e (BETA ONLY) Enable with 1.  Language selection only.
- -o (BETA ONLY) Enable with 1.  Encodes audio, passes thru video, selects audio/subtitle tracks.

# Comments
dovi_tool usage has been deprecated in favor of identical functionality added to Jellyfin-ffmpeg starting in 7.0.2-4.  This, and other changes, has allowed for significant stream lining of the various work flows.

Upstream ffmpeg has a similar, but not equivalent, functionality in their master branch.  But that functionality has not made it into a release, as far as I can tell.  Additionally, the syntax to activate the feature is different than Jellyfin-ffmpeg.
