# tmux-thumbs

![](https://travis-ci.com/fcsonline/tmux-thumbs.svg?branch=master)

A lightning fast version of [tmux-fingers](https://github.com/Morantron/tmux-fingers) written in [Rust](https://www.rust-lang.org/) for copy pasting with vimium/vimperator like hints.

## Usage

Press ( <kbd>prefix</kbd> + <kbd>Space</kbd> ) to highlist in you current tmux
visible pane all text that match specific pattern. The press the highlighted
letter hint to yank the text in your tmux buffer.

### Matched patterns

- File paths
- File in diff
- Git SHAs
- Colors in hex
- Numbers ( 4+ digits )
- Hex numbers
- IP4 addresses
- kubernetes resources
- UUIDs

Those are the list of mattched patterns that will be highlighted by default. If
you want to highlight a pattern that is not in this list you can add one or
more with `--regexp` parameter.

## Demo

[![demo](https://asciinema.org/a/232775.png)](https://asciinema.org/a/232775?autoplay=1)

## Tmux integration

Clone the repo:

```
git clone https://github.com/fcsonline/tmux-thumbs ~/.tmux/plugins/tmux-thumbs
```

Source it in your `.tmux.conf`:

```
run-shell ~/.tmux/plugins/tmux-thumbs/tmux-thumbs.tmux
```

Reload TMUX conf by running:

```
tmux source-file ~/.tmux.conf
```

## Install

The easiest way right now is to install with [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html):

```
cargo install tmux-thumbs
tmux-thumbs -
```

or download the source code and compile it:

```
git clone git@github.com:fcsonline/tmux-thumbs.git && cd tmux-thumbs
cargo build --release
```

## Configuration

If you want to customize how is shown your tmux-thumbs hints you can run the
command `tmux-thumbs` directly and play with all available parameters to set
your perfect profile.

Once completed, write those parameters in
`~/.tmux/plugins/tmux-thumbs/tmux-thumbs.sh` file. There is a `COMMAND`
variable where you can set all those options.

Example:

```
tmux-thumbs -a qwerty -r -u
```

You can review all available options executing:

```
> tmux-thumbs --help

tmux-thumbs 0.2.2
A lightning fast version of tmux-fingers, copy/pasting tmux like vimium/vimperator

USAGE:
    tmux-thumbs [FLAGS] [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -r, --reverse    Reverse the order for assigned hints
    -u, --unique     Don't show duplicated hints for the same match
    -V, --version    Prints version information

OPTIONS:
    -a, --alphabet <alphabet>                          Sets the alphabet [default: qwerty]
        --bg-color <background_color>                  Sets the background color for matches [default: black]
        --command <command>                            Pick command [default: tmux set-buffer {}]
        --fg-color <foreground_color>                  Sets the foregroud color for matches [default: green]
        --hint-bg-color <hint_background_color>        Sets the background color for hints [default: black]
        --hint-fg-color <hint_foreground_color>        Sets the foregroud color for hints [default: yellow]
    -p, --position <position>                          Hint position [default: left]
    -x, --regexp <regexp>...                           Use this regexp as extra pattern to match
        --select-fg-color <select_foreground_color>    Sets the foregroud color for selection [default: blue]
        --upcase-command <upcase_command>              Upcase command [default: tmux paste-buffer]

```

### Arguments

- **alphabet:** Choose which set of characters is used to build hints. Default [qwerty]
- **reverse:** Choose in which direction you want to assign hints. Useful to get shorter hints closer.
- **unique:** Choose if you want to assign the same hint for the same matched strings.
- **position:** Choose where do you want to show the hint in the matched string. Options (left, right). Default [left]
- **regexp:** Add extra pattern to match. This paramenter can have multiple instances.
- **command:** Choose whish command execute when you press a hint
- **upcase-command:** Choose which command execute when you press a upcase hint

- **bg-color:** Sets the background color for matches [default: black]
- **fg-color:** Sets the foregroud color for matches [default: green]
- **hint-bg-color:** Sets the background color for hints [default: black]
- **hint-fg-color:** Sets the foregroud color for hints [default: yellow]
- **select-fg-color:** Sets the foregroud color for selection [default: blue]

#### Alphabets

This is the list of available alphabets:

- `numeric`: 1234567890
- `abcd`: abcd
- `qwerty`: asdfqwerzxcvjklmiuopghtybn
- `qwerty-homerow`: asdfjklgh
- `qwerty-left-hand`: asdfqwerzcxv
- `qwerty-right-hand`: jkluiopmyhn
- `azerty`: qsdfazerwxcvjklmuiopghtybn
- `azerty-homerow`: qsdfjkmgh
- `azerty-left-hand`: qsdfazerwxcv
- `azerty-right-hand`: jklmuiophyn
- `qwertz`: asdfqweryxcvjkluiopmghtzbn
- `qwertz-homerow`: asdfghjkl
- `qwertz-left-hand`: asdfqweryxcv
- `qwertz-right-hand`: jkluiopmhzn
- `dvorak`: aoeuqjkxpyhtnsgcrlmwvzfidb
- `dvorak-homerow`: aoeuhtnsid
- `dvorak-left-hand`: aoeupqjkyix
- `dvorak-right-hand`: htnsgcrlmwvz
- `colemak`: arstqwfpzxcvneioluymdhgjbk
- `colemak-homerow`: arstneiodh
- `colemak-left-hand`: arstqwfpzxcv
- `colemak-right-hand`: neioluymjhk

#### Colors

This is the list of available colors:

- black
- red
- green
- yellow
- blue
- magenta
- cyan
- white
- default

## Extra features

- **Arrow navigation:** You can use the arrows to move arround between all matched items.
- **Auto paste:** If your last typed hint character is uppercase, you are going to pick and paste the desired hint.


## Contribute

This project started as a side project to learn Rust, so I'm sure that is full
of mistakes and areas to be improve. If you think you can tweak the code to
make it better, I'll really appreaciate a pull request. ;)

# License

[MIT](https://github.com/fcsonline/tmux-thumbs/blob/master/LICENSE)
