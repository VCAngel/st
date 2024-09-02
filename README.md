# Angel's settings for (suckless) st :frog:

This is my build for the [suckless terminal (st)](https://st.suckless.org/)! ヽ(°〇°)ﾉ

- Using [st v0.9.2](https://git.suckless.org/st) :rocket:

> Some features are proudly stolen from [Luke Smith's build](https://github.com/LukeSmithxyz/st) >:)

## Nice stuff (´・ω・`)

- Compatibility with `Xresources` and `pywal` for dynamic colors.
- Transparency/alpha, which is also adjustable from your `Xresources`.
- Default font is system "mono" at 14pt, meaning the font will match your
  system font.

## [dmenu](https://tools.suckless.org/dmenu/) features

- **follow urls** by pressing `alt-l`
- **copy urls** in the same way with `alt-y`
- **copy the output of commands** with `alt-o`

## Keyboard bindings

- **scrolling**:
  - `alt-↑/↓` or `alt-j/k` a la vim 🍷
  - `alt-pageup/down` or `alt-u/d`
  - `shift` + mouse wheel
- **zoom/change font size**:
  - `shift` + same bindings as above
  - `shift-alt-home` to reset to default
- **copy/paste**:
  - `alt-c` to copy
  - `alt-v` or `shift-insert` to paste

## Active patches

- Boxdraw
- Ligatures
- font2
- [st-undercurl](https://st.suckless.org/patches/undercurl/) v0.9-20240103
- [st-anysize](https://st.suckless.org/patches/anysize/) v20220718-baa9357

## But how do I install this? (・・ ) ?

You should have xlib header files and libharfbuzz build files installed.

```sh
git clone https://github.com/VCAngel/st
cd st
sudo make install
```

`make` is required for the build process!

`fontconfig` is required for the default build, since it asks `fontconfig`
for your system monospace font. Also, `libX11` and `libXft` are required
as well. Chances are you have these installed already.
If not, be sure to install them! (´・ω・`)

On OpenBSD, be sure to edit `config.mk` first and remove `-lrt` from the
`$LIBS` before compiling.

If transparency is wanted, (`xcompmgr`, `picom`, etc.) must be installed.

### When making changes \_\_φ(．．)

Applied a patch? Changed some settings in `config.h`? Do not forget to recompile!

Do this:

```sh
sudo make clean
make
sudo make install
```

Now you try your changes! (ง •\_•)ง

**Note**: `config.def.h` contains the default settings.

## Using Xresources

For many key variables, this build of `st` will look for X settings set in
either `~/.Xdefaults` or `~/.Xresources`. You must run `xrdb` on one of these
files to load the settings.

For example, you can define your desired fonts, transparency or colors:

```
*.font: Liberation Mono:pixelsize=12:antialias=true:autohint=true;
*.alpha: 0.9
*.color0: #111
...
```

The `alpha` value (for transparency) goes from `0` (transparent) to `1`
(opaque). There is an example `Xdefaults` file in this respository.

### Colors

About the color settings:

- This build will use gruvbox colors by default and as a fallback.
- If there are Xresources colors defined, those will take priority.
- But if `wal` has run in your session, its colors will take priority.

Note that when you run `wal`, it will negate the transparency of existing windows, but new windows will continue with the previously defined transparency.

## Contact ( ´ ▽ ` )

- Angel Vargas <vcangel00@gmail.com>
- [vcangel.dev](https://vcangel.dev)
