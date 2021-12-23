# dmlb
Initally a logbook for me, a person with type one diabetes mellitus, for blood glucose, insulin, and macronutrients. This evolved over time into a TeX project- making it prettier and/or easier to use. Mostly everything is commented in `dmlb.sty`, `template.tex`,and `graphmedaddy.tex`, to allow somebody to extend it to, say, have less columns, record and possibly graph values from additional or other columns.

If you need help with anything related to the package, open up an issue.

## Usage
Assuming you've just cloned the repo, or downloaded or extracted the [CTAN package](https://ctan.org/pkg/diabetes-logbook),

### Customization. To your satisfaction customize and edit:
- the colors: the default color scheme can be edited from the main .tex file, but, if you'd like a quick, no-fuss solution---the `[gray]` package option provides a grayscale color scheme (that you can edit), just comment out the `% COLORS` section in the main file;
-- page geometry (I can assure it works with A4 ISO standard, some parameters (like `\mym`) may need tweeking);
- data and graphing auxiliary file destination; default: `./graphs/`;
- y-axis (blood sugar) scale compression by `\mya` units, starting at `\myb` (positive real or int); `\myc` currently unused;

### Main:
- before the first entry, be it from an input file or from the main .tex one, set the date accordingly using `\dmlbsetdate{YYYY-MM-DD}[DIR]`, otherwise it'll be `0-00-00`; the optional argument is an absolute or relative path to a directory containing files named `YY-MM.tex`, which are to contain only `\QQQ` commands, possibly `\dmlbsetdate` for dates without a single `\QQQ`, or comments; these files will chronologically month- then year-wise be input; name files accordingly or edit the .sty file; lastly, be wary of recursively loading from relative paths (haven't tested myself);
- **!**: end the last *astonomical* entry (can be at the lastest `23:59`) with an asterisk `*` to not append those entries to new date, to keep correct track of the date (and more); if data are missing, or if you would like to skip a day or longer, even years (chronologicity must be kept), append the last entry with an asterisk `*` and use `\dmlbsetdate` to keep track the date;
- if you're gonna use two headers, such that the first takes up more rows than the second, adjust `\global\advance\row ...\relax` with the difference. Not configured for no headers yet, I think; default as provided works fine;
- main command is `\QQQ`: it inputs a new entry/row in the logbook; a single `{` or `}` more or less and it won't compile; I recommend a snippet to facilite data entry and error reduction, if you're text editor supports them;
- data is paritioned in `\myd`-day chunks- one per graph, of which there are 5 per page w/ default everything;
- run main without `[graph]` option to get .dat's (error, but should compile, if run with graph opt and no pdfs exist);

### Graphics:
- compile once wihout the `[graph]` packtion option;
- through a terminal emulation, run ` -shell-escape graphmedaddy.tex`, where the `` is either `pdflatex` or `xelatex`;
- if previous data have been changed, or would like to rerender them, or if dealing with the present, delete all respective files in the auxiliary data directory or uncomment `force remake` in the .sty, otherwise previously rendered .pfds will be inserted;
- rebuild main with the `[graph]` package option;
- labels for each next day, i.e., before the actual entry, and pdfbookmarks for all years, months, and graphs- anchors being `yyyy-mm-dd` resp. `gr:#`, starting from 1;

### Examples
Not fullly up to date though still  representative:
[".tex commented out"](../blob/master/templateGRAY.pdf)
[".tex color"](../blob/master/template.pdf)

## FIXME:
- migrate from tikz/pgf to matplotlib, or sth else; interalized graphics necessary at all?
- reduce user overhead;
- Fix issue with date vertical positioning with different hmargins, page size, and/or m-column width;
