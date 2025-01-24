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
- -a Enable with 1.  Intended for Anime.  Modifies language selection to also select Japanese in addition to English audio/subtitle tracks.

# Comments
dovi_tool usage has been deprecated in favor of identical functionality added to Jellyfin-ffmpeg starting in 7.0.2-4.  This, and other changes, has allowed for significant stream lining of the various work flows.

Upstream ffmpeg has a similar, but not equivalent, functionality in their master branch.  But that functionality has not made it into a release, as far as I can tell.  Additionally, the syntax to activate the feature is different than Jellyfin-ffmpeg.
