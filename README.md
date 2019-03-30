# dmlb
Initally a logbook for me, a person w/ type one diabetes mellitus, it evolved over time into a TeX project- making it prettier and/or easier to use, and currently I'd like to make it as simple as possible to use logbook for anybody, although the template and graphing things will be for T1DM.

## FIXME:
1. migrate from tikz/pgf to matplotlib, or sth else?;
2. more graphing options, more customization options;
3. optimize and make less bad
4. reduce user overhead;

## Usage
1. To your desire customize: colors (default's black-white-grey); (for now) graph width/height; page geometry; auxiliary file destination.
2. Before first entry/file(s), set date; otherwise it'll be `0-00-00`, can set year, month, day independently of one another if you skip days and/or months and/or years. File input take file(s) from rel. path named in `yy-mm.tex` form, in chron. order, i.e., if you have January, Februar and April, the latter won't be input, without the date being explicitly, appropriately set beforehand.
3. If you're gonna use two headers, such that the first takes up more rows than the second, adjust  `\global\advance\row ...\relax` with the difference. Not configured for no headers yet.
4. Main cmd is `\QQQ`- inputs new entry; use snippet along the lines of the one provided to facilitate data entry, speed, and error reduction via `%`- one extra or one less curly boi and it doesn't compile.
5. An opt eighth arg of a star, `*`, on the last entry of each *astronomical* day is **mandatory** for correct time/date representation in the .dat files.
6. To graph- periods to be graphed in format `yyyy-mm-dd` with `\tograph{}{}` will have their time/date and blood glucose vals output to `.dat`s; run main with to-be-graphed periods to get .dat's, run graphmedaddy with `graph`, and rerun main w/ `graph` too, and violá input- don't change, or comment out the to-be-graphed periods if you're gonna be inputing them in every build, if you change periods, delete everything in your folder for graphs `./myRelPath`.
7. Labels and pdfbookmarks for all dates and graphs- `yyyy-mm-dd` resp. `gr:#`, starting from 1, corresponding to first to be graphed period.