# onelight.vim
This is a fork version of [rakr/vim-one](https://github.com/rakr/vim-one),
that aims to be optimized for light theme.

## Vim Airline theme

Add the following line to your `~/.vimrc` or `~/.config/nvim/init.vim`

```vim
let g:airline_theme='onelight'
```

As for the colorscheme, this theme comes with light and dark flavors.

## Vim Lightline theme

Add the following line to your `~/.vimrc` or `~/.config/nvim/init.vim`

```vim
let g:lightline.colorscheme='onelight'
```

As for the colorscheme, this theme comes with light and dark flavors.
## List of enhanced language support

Pull requests are more than welcome here.
I have created few issues to provide a bare bone roadmap for this color
scheme.

### Stable

* Asciidoc
* CSS and Sass
* Cucumber features
* Elixir
* Go
* Haskell
* HTML
* JavaScript, JSON
* Markdown
* PureScript (thanks: [Arthur Xavier](https://github.com/arthur-xavier))
* Ruby
* Rust (thanks: [Erasin](https://github.com/erasin))
* Vim
* XML

### In progress

* Jade
* PHP
* Python


## Installation

You can use your preferred Vim Package Manager to install **onelight**.

## Usage

**onelight** comes in two flavors: light and dark.

```vim
colorscheme onelight
```

`set background` has to be called after setting the colorscheme, this explains
the issue [#21][issue_21] where Vim tries to determine the best background when `ctermbg`
for the `Normal` highlight is defined.

### Italic support

Some terminals do not support italic, cf. [#3][issue_3].

If your terminal does support _italic_, you can set the `g:onelight_allow_italics` variable to 1 in your `.vimrc` or `.config/nvim/init.vim`:

```vim
let g:onelight_allow_italics = 1 " I love italic for comments
colorscheme onelight
```

iTerm2 can support italic, follow the instructions given in this [blog post by Alex Pearce](https://alexpearce.me/2014/05/italics-in-iterm2-vim-tmux/).
Make sure to read the update if you are using tmux version 2.1 or above.

### True color support
To benefit from the **true color** support make sure to add the following lines in your `.vimrc` or `.config/nvim/init.vim`

```vim
"Credit joshdick
"Use 24-bit (true-color) mode in Vim/Neovim when outside tmux.
"If you're using tmux version 2.2 or later, you can remove the outermost $TMUX check and use tmux's 24-bit color support
"(see < http://sunaku.github.io/tmux-24bit-color.html#usage > for more information.)
if (empty($TMUX))
  if (has("nvim"))
    "For Neovim 0.1.3 and 0.1.4 < https://github.com/neovim/neovim/pull/2198 >
    let $NVIM_TUI_ENABLE_TRUE_COLOR=1
  endif
  "For Neovim > 0.1.5 and Vim > patch 7.4.1799 < https://github.com/vim/vim/commit/61be73bb0f965a895bfb064ea3e55476ac175162 >
  "Based on Vim patch 7.4.1770 (`guicolors` option) < https://github.com/vim/vim/commit/8a633e3427b47286869aa4b96f2bfc1fe65b25cd >
  " < https://github.com/neovim/neovim/wiki/Following-HEAD#20160511 >
  if (has("termguicolors"))
    set termguicolors
  endif
endif


colorscheme onelight
```
### Tmux support
To get true color working in tmux, ensure that the `$TERM` environment variable is set to `xterm-256color`. Inside the `.tmux.conf` file we need to override this terminal and also set the default terminal as 256 color.

```
# Add truecolor support
set-option -ga terminal-overrides ",xterm-256color:Tc"
# Default terminal is 256 colors
set -g default-terminal "screen-256color"
```

Note that this only works for Neovim (tested on 0.1.5). For some reason Vim (7.5.2334) doesn't play nice. See [blog post by Anton Kalyaev](http://homeonrails.com/2016/05/truecolor-in-gnome-terminal-tmux-and-neovim/) for more details on setting up tmux.

For Vim inside tmux, you can add the following snippet in your `~/.vimrc`

```viml
set t_8b=^[[48;2;%lu;%lu;%lum
set t_8f=^[[38;2;%lu;%lu;%lum
```

Note: the `^[` in this snippet is a real escape character. To insert it, press `Ctrl-V` and then `Esc`.

I've tested the following setup on a Mac:

* iTerm2 nightly build
* Neovim 0.1.4 and 0.1.5-dev
* Vim 7.4.1952

## Contributors

A special thank you to the following people

* [laggardkernel](https://github.com/laggardkernel): Startup time improvement
* [Erasin](https://github.com/erasin): Rust support
* [Malcolm Ramsay - malramsay64](https://github.com/malramsay64): Gracefully fail if colorscheme is not properly loaded
* [Arthur Xavier](https://github.com/arthur-xavier): PureScript support
* [keremc](https://github.com/keremc): Tip Vim true color support inside tmux
* [jetm](https://github.com/jetm): C/C++ highlighting

[issue_3]: https://github.com/rakr/vim-one/issues/3
[issue_21]: https://github.com/rakr/vim-one/issues/21
