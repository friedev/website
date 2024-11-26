
vw (vim wiki) is yet another system for maintaining a simple personal wiki using vim and markdown.

vw was made by [Aaron Friesen](https://frie.dev) for [CornHacks 2023](https://unlcornhacks.com), where it won 3rd place.

## Dependencies

- To compile to HTML:
	- make
	- [lowdown](https://kristaps.bsd.lv/lowdown/)
- To import from TiddlyWiki:
	- Python 3

## Quick Start

Clone vw:

```
git clone https://frie.dev/vw.git
```

Create a new wiki by copying the example:

```
cp -r vw/example my_wiki
```

Now you can create and edit articles in `my_wiki/md/` as you see fit.

### Extras

Install the `vw` helper script:

```sh
cp vw/vw ~/.local/bin
```

Add the "insert link" macro to your vimrc:

```sh
cat vw/insert_link.vim >> ~/.vimrc
```

Start tracking the history of your wiki's articles:

```
git init my_wiki
```

Compile your wiki to HTML:

```
make -C my_wiki
```

## Architecture

vw is not a single piece of software, but rather a process and a small collection of tools.
A vw wiki is a collection of markdown files in a directory that can link to one another.
Each file represents an article in the wiki.

### File Naming

The recommended naming convention for vw wikis, and the one used by the included tools, is as follows.
The name of each file should be the article title converted to lowercase, with spaces converted to underscores, and with the `.md` file extension.

### Navigation

To create links between pages, use the normal markdown syntax:

```md
[vw](vw.md) is a tool for creating wikis.
```

vw will translate each link to point to its corresponding HTML page when you run `make`.

Vim provides some useful built-in keybinds that you can use to navigate the wiki.
To open a link in a new buffer, move the cursor over it and type `gf`.
To open an external link in the proper program (like your browser), type `gx` instead.

### Version Control

To edit collaboratively and track the history of your articles, you can simply create a git repo at the root level of your wiki.
For the most granular control, like you would get in a traditional wiki, make a commit after each edit you make to a page.
However, unlike a traditional wiki, you can also choose to group related changes to multiple pages together into a single commit, like you might do in a software project.

## Tools

### HTML Export

vw includes a makefile which you can use to compile your wiki to HTML.
This lets you browse your wiki locally with a web browser, or publish it to a website.
You can customize this build process to your liking simply by editing the makefile.

The makefile includes options for common use cases, such as adding a CSS stylesheet or a common header and footer.
More details about setting these options can be found in comments in the makefile.

### Helper Script

vw includes a shell script (also named `vw`) which you can use to refactor your wiki and generate various insights.
For more detailed help information, run `vw` with no arguments.
For maximum usability, add `vw` to your path; for instance, you could copy it to `~/.local/bin` or `/usr/local/bin`.

**NOTE:** `vw` must be run from the same directory as your wiki's markdown files.

### Link Generation

To speed up editing, vw includes a vim macro that inserts the link corresponding to the article title under the cursor.
For example, if you typed `[My Article]`, running the macro would yield `[My Article](my_article.md)`.
To install it, append it to your vimrc.

```sh
cat vw/insert_link.vim >> ~/.vimrc
```

Alternatively, check out [vim-markdown-wiki](https://github.com/mmai/vim-markdown-wiki), which provides similar functionality in the form of a Vim script plugin.
Note that, by default, vim-markdown-wiki replaces spaces with hyphens rather than underscores.

### Import from TiddlyWiki

To convert a TiddlyWiki to a vw wiki, you can use the included Python script: `tiddlers_to_vw.py`.
The converter doesn't handle all of TiddlyWiki's features, but it should still save you time compared to manual conversion.

## Alternatives

Many similar projects of varying complexity attempt to solve the same problem as vw.
Some are listed below, roughly in order of similarity to vw.
I recommend trying them out and deciding which you prefer.

- [vim-markdown-wiki](https://github.com/mmai/vim-markdown-wiki)
- [wiki.vim](https://github.com/lervag/wiki.vim)
- [Vim-Waikiki](https://github.com/fcpg/vim-waikiki)
- [SoyWiki](https://github.com/danchoi/soywiki) (unmaintained)
- [vimwiki](https://vimwiki.github.io/)
