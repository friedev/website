
HyperRogue Challenger is a program that generates random challenges for the game [HyperRogue](https://www.roguetemple.com/z/hyper/) by [Zeno Rogue](https://www.roguetemple.com/z/). Challenges can be generated in a bingo card format, or independently in a list format. These challenges can be used to spice up a regular solo run, or you can challenge a friend!

## Features

- Generate multiple unique challenges
- Hundreds of potential challenges
- Constraints: impose restrictions in addition to the challenges
- Cursed mode: extra hard and/or weird challenges (sanity not guaranteed)
- Bingo mode: generates challenges in a 5x5 bingo card format
	- ASCII table view
	- PDF export with PDFLaTeX
	- PNG export with ImageMagick
	- Copy PDF/PNG to Wayland clipboard

## Dependencies

- **Required:** Python 3
- *Optional:* LaTeX (e.g. TeXLive) and PDFLaTeX - for PDF bingo card export
- *Optional:* ImageMagick - for PNG bingo card export (requires LaTeX)
- *Optional:* `wl-clipboard` - for automatically copying the PNG (requires LaTeX and ImageMagick)

## Usage

To install, simply clone the repository, install the required dependencies, and install any optional dependencies you want.

To run, execute `python3 hyperrogue_challenger.py` from within the repository directory.

For detailed, auto-generated usage information, run `python3 hyperrogue_challenger.py --help`.

## Suggested Bingo Rules

Play with one or more other players and share the same bingo card. To win, one player must get a bingo on the generated bingo card. Multiple players may complete the same challenge and each may count it towards a bingo. If you get checkmated, you can restart from the beginning of the game. You don't lose any completed challenges, but you do lose progress towards uncompleted challenges.

**More Competitive Variant:** Only the first player to complete a given challenge can count it towards a bingo.

**Hardcore Variant:** If you get checkmated, you can restart from the beginning of the game. However, you lose all completed challenges; in other words, you must get a bingo in a single run.

Challenges can also be played in shoot-em-up mode (which is generally easier) or in other modes if you desire.

## Troubleshooting

If you get an error about converting PDF to JPG, comment out any GhostScript-related (`gs`) or PDF-related (`pdf`, `ps`) entries in `/etc/ImageMagick-7/policy.xml`, such as any of the following (I've only ever seen the first one):

```xml
<policy domain="delegate" rights="none" pattern="gs" />
<policy domain="coder" rights="read | write" pattern="PDF" />
<policy domain="coder" rights="none" pattern="{PS,PS2,PS3,EPS,PDF,XPS}" />
```

## License

HyperRogue Challenger is licensed under the [GNU General Public License Version 2](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html), which is the same license that HyperRogue uses. See `LICENSE.txt` for the full license text.
