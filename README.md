sprunge
=======

## Overview

A script for fetching or posting text pastes on http://sprunge.us.

## Usage & Options

    usage: sprunge [-h] [--clip-command clip_command] [--clipboard] [id]

    Upload text from stdin to http://sprunge.us. If [id] is provided,
    the corresponding paste is fetched and displayed.

    positional arguments:
      id                    when provided, fetches and displays a sprunge paste

    optional arguments:
      -h, --help            show this help message and exit
      --clip-command clip_command, -cc clip_command
                            clipboard command (default: SPRUNGE_CLIPPER)
      --clipboard, -c       pipe stdout to --clip-command

    environment variables:
      SPRUNGE_CLIPPER (default: 'xclip -sel primary')
      SPRUNGE_SERVER_TIMEOUT (default: 5)

## Upload A Paste

To upload a paste, pipe some text via `stdin` to `sprunge`.

    $ cat file.txt | sprunge
    http://sprunge.us/fedG
    $ sprunge < file.txt
    http://sprunge.us/aBCd

An uploader can automatically copy the resulting paste URL to clipboard with `--clipboard|-c`.

    $ cat file.txt | sprunge --clipboard
    http://sprunge.us/xyzF
    $ cat file.txt | sprunge -c
    http://sprunge.us/PnoK

The clipboard command can be customized via `--clip-command|-cc`.

    $ cat file.txt | sprunge -cc 'xclip -sel clipboard' -c
    http://sprunge.us/bLaH

## Fetch A Paste

Already uploaded pastes can be fetched by passing the paste ID to sprunge as a positional argument.

    $ echo 'test' | sprunge
    http://sprunge.us/aBCdeFG
    $ sprunge aBCdeFG
    test
    $ sprunge http://sprunge.us/aBCdeFG
    test

## Configuration

A few environment variables are utilized for defaults.

* `SPRUNGE_SERVER_TIMEOUT`: The sprunge request timeout (default: 5)
* `SPRUNGE_CLIPPER`: Default --clip-command