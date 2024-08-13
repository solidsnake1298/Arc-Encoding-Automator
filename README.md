# Arc-Encoding-Automator
Automates media encoding to AV1, including handling language selection, converting Dolby Vision to HDR10, and converting Dolby/DTS audio to FLAC/OPUS.

# Requirements
- Linux kernel 6.2+.
- ffmpeg, but tested with Jellyfin-ffmpeg 6.0.1, symlinked to /usr/bin.
- Intel Arc GPU.  May work with Meteor Lake Intel CPUs, but will require kernel 6.7 and newer.
- dovi_tool installed to /usr/bin - https://github.com/quietvoid/dovi_tool
- jq - Available in most package repos.
- bc - Available in most package repos.
- parallel - Available in most package repos.

# Options
- -i Input file (required)
- -c Number of chapters per episode when splitting monolithic TV show files.
- -s Season number for output file name (WIP), requires usage of -c.
- -e Starting episode number for output file name (WIP), requires usage of -c.
- -d Enable with 1.  Converts Dolby Vision to HDR10 by removing the DV side channel.  Tested with DV 7.6 and 8.1.  Requires dovi_tool be installed.
- -a Enable with 1.  Intended for Anime.  Modifies language selection to also select Japanese in addition to English audio/subtitle tracks.
- -r Defaults to 0 (do nothing).  Currently has 1, 2, and 3 as options.  This is deprecated and was a hack.  Planning to remove.
- -f Enable with 1.  When enabled all selected audio tracks are converted to FLAC or OPUS.  Lossless codecs, like Dolby TrueHD or DTS-HD MA, are converted to FLAC.  Lossy codecs are converted to OPUS.
- -o Enable with 1.  When enabled, only the audio is processed.  Without -f only English and/or Japanese track selection is performed.
