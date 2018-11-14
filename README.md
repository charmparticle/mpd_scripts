# mpd_scripts
some scripts for mpd, the music player daemon:

**playpls:**

  requires: [slmenu](https://bitbucket.org/rafaelgg/slmenu). Get that before running this script.
  playpls plays pls or m3u files in your ~/tunes folder. If you don't have a tunes folder, run the update-radio script first.

  Examples:

    #show the urls contained in a playlist with the string "sonic" in the filename
    $ playpls -s sonic
    #add kexp internet radio to the playlist
    $ playpls -a kexp
    #show the available streams
    $ playpls

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

  or a bunch of uniquely named mp3 files which have been tagged properly.
                            
  if you just have a bunch of loose mp3 files with no tags, you'll only get a random song instead of a random album.

  Examples:

    #print a random album by Miles davis to stdout
    $ randalbum -t "Miles Davis" -s
    #this could be used on conjunction with mpc:
    $ randalbum -t "Miles Davis" -s | mpc add
    #play a random album
    $ randalbum
    #select an album for a random artist, and play it:
    #(uses slmenu, so you need to have that installed to use this feature)
		$ randalbum --select-album
