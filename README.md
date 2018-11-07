# mpd_scripts
some scripts for mpd, the music player daemon:

**playpls:**

playpls plays pls or m3u files in your ~/tunes folder. If you don't have a tunes folder, run the update-radio script first.

**update-radio**

creates a ~/tunes folder if you don't have one already, and downloads a bunch of internet radio stations to them. You are free to add more of your own or to change the configuration or whatever -- everyone's musical tastes are different; I wrote this mainly for myself.

**mpcvol**

mpcvol allows you to easily change the volume of whatever music you're listening to on mpd.

**randalbum**

this script adds a random album to your mpd playlist, or clears your mpd playlist, adds the random album, and plays it, or simply prints the name of a random album in your library, depending on the arguments you pass. With no arguments, it will clear your mpd playlist, add a random album, and play it. It's worth noting that this script was written with the assumption that your music library is laid out like so:
    $Musicdir/
             /(artists)/
                     /(albums)/
                            /(folders or mp3 files)
    or
    
    $Musicdir/
         /(albums)/
                            
if you just have a bunch of loose mp3 files with no tags, you'll only get a random song instead of a random album.
