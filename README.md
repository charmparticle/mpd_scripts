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

  this script adds a random album to your mpd playlist, or clears your mpd playlist, adds the random album, and plays it, or simply prints the name of a random album in your library, depending on the arguments you pass. With no arguments, it will clear your mpd playlist, add a random album, and play it. It's worth noting that this script was written with the assumption that your music library is laid out with artists as the top level category

  Examples:

    #print a random album by Miles davis to stdout
    $ randalbum -t "Miles Davis" -s
    #this could be used on conjunction with mpc:
    $ randalbum -t "Miles Davis" -s | mpc add
    #although, it's faster to juse use the add option
    $ randalbum -t "Miles Davis" -a
    #play a random album
    $ randalbum
    #play random music that has 'guitar' in the name:
    $ randalbum -g 'guitar'
    #play 5 random pieces of music that have 'guitar' in the name:
    #worth noting, -n only works with -s or -a
    $ randalbum -g 'guitar' -s -n 5
    #select an album for a random artist, and play it:
    #(uses slmenu, so you need to have that installed to use this feature)
    $ randalbum --select-album
    #select a song from a random album, and play it. This uses slmenu,
    #and if you type, it will intelligently autocomplete
    $ randalbum --select-song
    #select an artist, then an album, then a song, and print it out
    #at this point, you might as well use ncmpcpp instead.
    $ randalbum -st -sm -sg -s

**fadein**

Fades in music that's piped in from one of the other scripts or something else.

Examples:

    # fade in a random Brian Eno album, using linear fade-in, to a max volume of 56
    $ randalbum -t 'Brian Eno' -s | fadein -lin -m 56 -
    # fade in an internet radio stream, using logarithmic fade-in, to a max volume of 55
    $ playpls -s e24 | fadein -

**mpcplay**

This script simply adds and plays any music uri that is supplied to it. This allows you to set mpd as your default music program.

Example:

    # add a playlist and play it:
    $ mpcplay $(playpls -s sonic)
