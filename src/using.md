# Basic Usage

### set up

---

first off, you'll need Linux and GNU make. things might work on *nix without GNU tools, but no promises. for markdown support, you'll need [kramdown](https://kramdown.gettalong.org/).  
clone this [example site repository](https://git.ceionia.com/lucia/LucysSSG), or get the base Makefile [here](Makefile).  
your input files go in the `src/` directory. modify the `files` field at the top of the Makefile to add new outputs.  
for example, to produce `out/index.html` and `out/site.css` from `src/index.md` and `src/site.css`, your files field should look like this:  
```
files = index.html site.css  
```
  
the default Makefile uses `templates/base-start.html` and `templates/base-end.html` at the start and end of each `.html` output file. simply remove the default template rule ([see template guide](templates.html)) to stop this.  
  
  
  
### building your site

---

run `make`. the makefile will generate your output files in `out/` by default (you can change this with the OUTDIR environment variable, `OUTDIR=../web make`, or directly in the Makefile).  
`make clean` will remove the OUTDIR.  
  
  
  
### hosting your site

---

i use [nginx](https://nginx.org/) on an [arch linux](https://archlinux.org/) server. if you don't have a server, i've heard good things about [neocities](https://neocities.org/), you should be able to just upload the files created by this.
