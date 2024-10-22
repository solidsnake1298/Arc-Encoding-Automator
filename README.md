# Arc-Encoding-Automator
Automates media encoding to AV1, including handling language selection, converting Dolby Vision to HDR10, and converting Dolby/DTS audio to OPUS.

# Requirements
- Linux kernel 6.2+.
- ffmpeg, but tested with Jellyfin-ffmpeg 6.0.1 and 7.0.2, symlinked to /usr/bin.
- Intel GPU with AV1 encoding support.
- Dolby Vision removal functionality requires Jellyfin-ffmpeg 7.0.2-4 and newer.
- jq - Available in most package repos.
- bc - Available in most package repos.

# Options
- -i Input file (required)
- -c Number of chapters per episode when splitting monolithic TV show files.
- -d Enable with 1.  Converts Dolby Vision to HDR10 by removing the DV side channel.  Tested with DV 7.6 and 8.1.  Requires Jellyfin-ffmpeg 7.0.2-4 and newer.
- -a Enable with 1.  Intended for Anime.  Modifies language selection to also select Japanese in addition to English audio/subtitle tracks.
- -f Enable with 1.  When enabled all selected audio tracks are converted to OPUS.  If lossless codecs, like Dolby TrueHD or DTS-HD MA, are present for the selected languages this script will ignore the remaining lossy tracks for that language.
- -o Enable with 1.  When enabled, only the language selection is performed.  Can be combined with -f and -a.  -d is ignored.

# Comments
dovi_tool usage has been deprecated in favor of identical functionality added to Jellyfin-ffmpeg starting in 7.0.2-4.  This, and other changes, has allowed for significant stream lining of the various work flows.

Upstream ffmpeg has a similar, but not equivalent, functionality in their master branch.  But that functionality has not made it into a release, as far as I can tell.  Additionally, the syntax to activate the feature is different than Jellyfin-ffmpeg.
