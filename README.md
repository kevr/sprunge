sprunge
=======

A script for fetching or posting text pastes on http://sprunge.us.

## Upload A Paste

To upload a paste, pipe some text via `stdin` to `sprunge`.

    $ cat file.txt | sprunge
    $ sprunge < file.txt

An uploader can automatically copy the resulting paste URL to clipboard with `--clipboard|-c`.

    $ cat file.txt | sprunge --clipboard
    $ cat file.txt | sprunge -c

The clipboard command can be customized via `--clip-command|-cc`.

    $ cat file.txt | sprunge -cc 'xclip -sel clipboard' -c

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