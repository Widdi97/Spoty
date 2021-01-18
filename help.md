# Spoty Help

Disclaimer: no return messages on discord yet!

## Bot CMD

Basic bot commands:

    $join - Bot joins current channel
    
    $leave - Bot leaves current channel
    
    $play - Bot start playback 
    
    $pause - pause current playback
    
    $resume - resumes current playback
    
    $commands - returns link to this helpfile
    
    $spt [SUBCOMMAND] [FLAGS] [OPTIONS] ...  - pass arguments to spt CLI

    

## spt help

Data Dump of [spotify-tui](https://github.com/Rigellute/spotify-tui) CLI help command:

## SUBCOMMANDS of spt:
    play        Plays a uri or another spotify item by name [aliases: p]
    playback    Interacts with the playback of a device [aliases: pb]

## - PLAY - 

If you specify a uri, the type can be inferred. If you want to play something by name, you have to specify the type:
`--track`, `--album`, `--artist`, `--playlist` or `--show`. The first item which was found will be played without
confirmation. To add a track to the queue, use `--queue`. To play a random song from a playlist, use `--random`. Again,
with `--format` you can specify how the output will look. The same function as found in `playback` will be called.

USAGE:
    spt play [FLAGS] [OPTIONS] <--uri <URI>|--name <NAME>>

FLAGS:
    -b, --album
            Looks for an album

    -a, --artist
            Looks for an artist

    -h, --help
            Prints help information

    -p, --playlist
            Looks for a playlist

    -q, --queue
            Adds track to queue instead of playing it directly

    -r, --random
            Plays a random track (only works with playlists)

    -w, --show
            Looks for a show

    -t, --track
            Looks for a track

    -V, --version
            Prints version information

OPTIONS:
    -d, --device <DEVICE>
            Specifies the spotify device to use

    -f, --format <FORMAT>
            There are multiple format specifiers you can use: %a: artist, %b: album, %p: playlist, %t: track, %h: show,
            %f: flags (shuffle, repeat, like), %s: playback status, %v: volume, %d: current device. Example: spt pb -s
            -f 'playing on %d at %v%' [default: %f %s %t - %a]
    -n, --name <NAME>
            Plays the first match with NAME from the specified category

    -u, --uri <URI>
            Plays the URI


## -  PLAYBACK - 

Use `playback` to interact with the playback of the current or any other device. You can specify another device with
`--device`. If no options were provided, spt will default to just displaying the current playback. Actually, after every
action spt will display the updated playback. The output format is configurable with the `--format` flag. Some options
can be used together, other options have to be alone.

Here's a list:

* `--next` and `--previous` cannot be used with other options
* `--status`, `--toggle`, `--transfer`, `--volume`, `--like`, `--repeat` and `--shuffle` can be used together
* `--share-track` and `--share-album` cannot be used with other options

USAGE:
    spt playback [FLAGS] [OPTIONS]

FLAGS:
    -h, --help
            Prints help information
            
    -n, --next
            This jumps to the next song if specied once. If you want to jump, let's say 3 songs forward, you can use
            `--next` 3 times: `spt pb -nnn`.
    -p, --previous
            This jumps to the beginning of the current song if specied once. You probably want to jump to the previous
            song though, so you can use the previous flag twice: `spt pb -pp`. To jump two songs back, you can use `spt
            pb -ppp` and so on.
        --repeat
            Switches between repeat modes

        --share-album
            Returns the url to the album of the current track

        --share-track
            Returns the url to the current track

        --shuffle
            Toggles shuffle mode

    -t, --toggle
            Pauses/resumes the playback of a device

    -V, --version
            Prints version information


OPTIONS:

    -f, --format <FORMAT>
            There are multiple format specifiers you can use: %a: artist, %b: album, %p: playlist, %t: track, %h: show,
            %f: flags (shuffle, repeat, like), %s: playback status, %v: volume, %d: current device. Example: spt pb -s
            -f 'playing on %d at %v%' [default: %f %s %t - %a]

    -v, --volume <VOLUME>
            Sets the volume of a device to VOLUME (1 - 100)
