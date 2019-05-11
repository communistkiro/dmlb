# dmlb
Initally a logbook for me, a person w/ type one diabetes mellitus, this evolved over time into a TeX project- making it prettier and/or easier to use, and currently I'd like to make it a as simple as possible to use logbook for anybody, although the template and graphing things will be for T1DM. 

The bulk of the the thing is wholly unnecessary, but yeah...

## Usage
Mostly everything is commented in `dmlb.sty`, `template.tex`,and `graphmedaddy.tex`, but more or less:

- To your desire customize: colors (default's black-white-grey); page geometry; auxiliary file destination; y-axis (blood sugar) scale compression by `\mya` units starting at `\myb`; `\myc` unused currently.
- Before first entry/file(s), set date using `\dmlbsetdate`; otherwise it'll be `0-00-00`; if you skip days, months, years, i.e., no entries for a period, end last entry with `*` to not append entries to new date, and set new date (has to be in chron. order). File input take file(s) from rel. path named in `yy-mm.tex` form, in sequentially in chron. order, i.e., if you have January, Februar and April, the latter won't be input, without the date being explicitly, appropriately set beforehand within the file.
- If you're gonna use two headers, such that the first takes up more rows than the second, adjust  `\global\advance\row ...\relax` with the difference. Not configured for no headers yet, I think.
- Main cmd is `\QQQ`- inputs new entry; use snippet along the lines of the one provided to facilitate data entry, and error reduction- one extra or one less curly boi and it doesn't compile.
- An opt eighth arg of a star, `*`, on the last entry of each *astronomical* (00:00--23:59) day is **mandatory** for correct time/date collection  in the .dat files, which is only necessary for the graphs.
- Data collection is automated in `\myd` days per graph, of which there are 5/page; run main without `[graph]` option to get .dat's (error, but should compile, if run with graph opt and no pdfs exist).
- Graphics: thru a CLI run `<tex engine> -shell-escape graphmedaddy.tex`, at least for windows with TeX Live (seach `latex shell escape` in the tex.stackexchange.com for more options); delete any previous pdfs of same name, if the periods or data have changed (or uncomment `force remake` in the .sty); rebuild main w/ `[graph]` option. As long as the .pdf's are to be found they'll get inserted.

Labels for each next day, i.e., before the actual entry, and pdfbookmarks for all years, months, and graphs- anchors being `yyyy-mm-dd` resp. `gr:#`, starting from 1.

## FIXME:
- date label placement at, not before, first entry
- make less bad;
- migrate from tikz/pgf to matplotlib, or sth else; interalized graphics necessary at all?
- implement optional graphing options for each to be graphed period;
- reduce user overhead(?);
- Fix issue with date vertical positioning with different hmargins, page size, and/or m-column width;
