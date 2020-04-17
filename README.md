# dmlb
Initally a logbook for me, a person w/ type one diabetes mellitus, this evolved over time into a TeX project- making it prettier and/or easier to use, and currently I'd like to make it a as simple as possible to use logbook for anybody, although the template and graphing things will be for T1DM. 

The bulk of the the thing is wholly unnecessary, but yeah...

## Usage
Mostly everything is commented in `dmlb.sty`, `template.tex`,and `graphmedaddy.tex`, but more or less:

- to your desire customize: 
-- colors (black-white-grey is defined in the sty, comment out or edit defs in .tex);
-- page geometry;
-- auxiliary file destination; y-axis (blood sugar) scale compression by `\mya` units starting at `\myb`; `\myc` unused currently;
- main 
-- before first entry or input file(s), set the date accordingly using `\dmlbsetdate`, otherwise it'll be `0-00-00`;
-- if you skip days, months, years, i.e., no entries for a period, end last entry with `*` to not append entries to new date, and set new date (has to be in chron. order). files are input from rel. path named in `yy-mm.tex` form, in sequentially in chron. order (mm going from 1 to 12, ultimately incrementing yy), i.e., name files appropriately or edit the .sty;
-- also, if data are missing, be it days, months or years, use `\dmlbsetdate` to keep date proper; 
-- if you're gonna use two headers, such that the first takes up more rows than the second, adjust  `\global\advance\row ...\relax` with the difference. Not configured for no headers yet, I think; default as provided works fine;
-- main cmd is `\QQQ`; it inputs new entry; preferrably use a snippet along the lines of the one provided to facilitate data entry, and error reduction- one extra or one less curly boi and it doesn't compile;
-- an optional eighth arg of a star, `*`, on the last entry of each *astronomical* (00:00--23:59) day is **mandatory** for correct time/date calculation, collection, representation in the .dat files and in the compilation of the pdf , (i believe);
-- data is paritioned in `\myd`-day chunks- one per graph, of which there are 5 per page w/ default everything;
-- run main without `[graph]` option to get .dat's (error, but should compile, if run with graph opt and no pdfs exist);
- graphics
-- having compiled once wihout the `[graph]` opt, thru a terminal run `<tex engine> -shell-escape graphmedaddy.tex`, where the tex engine is either pdflatex or xelatex;
-- delete any previous pdfs of same name, if the graph period or the data have changed (or uncomment `force remake` in the .sty); rebuild main w/ `[graph]` option. As long as the .pdfs are to be found they'll get inserted;
-- labels for each next day, i.e., before the actual entry, and pdfbookmarks for all years, months, and graphs- anchors being `yyyy-mm-dd` resp. `gr:#`, starting from 1;

## examples
not full up to date, still mostly representative
[".tex commented out"](../blob/master/templateGRAY.pdf)
[".tex color"](../blob/master/template.pdf)

## FIXME:
- migrate from tikz/pgf to matplotlib, or sth else; interalized graphics necessary at all?
- reduce user overhead;
- Fix issue with date vertical positioning with different hmargins, page size, and/or m-column width;
