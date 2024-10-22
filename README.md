# Arc-Encoding-Automator
<<<<<<< HEAD
Automates media encoding to AV1, including handling language selection, converting Dolby Vision to HDR10, and converting Dolby/DTS audio to OPUS.

# Requirements
- Linux kernel 6.2+.
- ffmpeg, but tested with Jellyfin-ffmpeg 6.0.1 and 7.0.2, symlinked to /usr/bin.
- Intel GPU with AV1 encoding support.
- Dolby Vision removal functionality requires Jellyfin-ffmpeg 7.0.2-4 and newer.
=======
Automates media encoding to AV1, including handling language selection, converting Dolby Vision to HDR10, and converting Dolby/DTS audio to FLAC/OPUS.

# Requirements
- Linux kernel 6.2+.
- ffmpeg, but tested with Jellyfin-ffmpeg 6.0.1, symlinked to /usr/bin.
- Intel Arc GPU.  May work with Meteor Lake Intel CPUs, but will require kernel 6.7 and newer.
- dovi_tool installed to /usr/bin - https://github.com/quietvoid/dovi_tool
>>>>>>> refs/remotes/origin/main
- jq - Available in most package repos.
- bc - Available in most package repos.

# Options
- -i Input file (required)
- -c Number of chapters per episode when splitting monolithic TV show files.
- -d Enable with 1.  Converts Dolby Vision to HDR10 by removing the DV side channel.  Tested with DV 7.6 and 8.1.  Requires Jellyfin-ffmpeg 7.0.2-4 and newer.
- -a Enable with 1.  Intended for Anime.  Modifies language selection to also select Japanese in addition to English audio/subtitle tracks.
<<<<<<< HEAD
- -f Enable with 1.  When enabled all selected audio tracks are converted to OPUS.  If lossless codecs, like Dolby TrueHD or DTS-HD MA, are present for the selected languages this script will ignore the remaining lossy tracks for that language.
- -o Enable with 1.  When enabled, only the language selection is performed.  Can be combined with -f and -a.  -d is ignored.

# Comments
dovi_tool usage has been deprecated in favor of identical functionality added to Jellyfin-ffmpeg starting in 7.0.2-4.  This, and other changes, has allowed for significant streaming lining.

Upstream ffmpeg has a similar, but not equivalent, functionality in their master branch.  But that functionality has not made it into a release, as far as I can tell.  Additionally, the syntax to activate the feature is different than Jellyfin-ffmpeg.
=======
- -r Defaults to 0 (do nothing).  Currently has 1, 2, and 3 as options.  This is deprecated and was a hack.  Planning to remove.
- -f Enable with 1.  When enabled all selected audio tracks are converted to FLAC or OPUS.  Lossless codecs, like Dolby TrueHD or DTS-HD MA, are converted to FLAC.  Lossy codecs are converted to OPUS.
- -o Enable with 1.  When enabled, only the audio is processed.  Without -f only English and/or Japanese track selection is performed.
>>>>>>> refs/remotes/origin/main
