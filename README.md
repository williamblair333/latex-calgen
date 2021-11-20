LaTeX Calendar Generator
========================

This tool uses python's
[calendar](http://docs.python.org/library/calendar.html) library (which
provides modular `ncal` functionality) to generate a TeX based, A4-sized wall
calendar with one month per page.

Prerequisites
-------------

* Python 3
* A working LaTeX installation, including `pdflatex`.

Usage
-----

	./make-calendar.py 2012 # will generate a calendar for 2012

The complete invocation syntax is

	./make-calendar.py <year> [csv-data [first-day-of-week]]

The second parameter `csv-data` is intended to be used for e.g. birthday data
and the csv should have three columns containing: 
- a description
- the date in `M/D/YYYY` format  
- a description for each data point


The first line of the CSV file is ignored


The third parameter `first-day-of-week` is used to select on which weekday
(0=Monday through to 6=Sunday) the week starts. If the parameter is omitted the
week starts on Monday.
If you don't want the week to start on Monday, but don't have any custom data,
just supply an empty file.

Example
-------
Date,2nd_entry,3rd_entry
dd-mm-yyyy,2nd entry,3rd entry

-<csv>-
Date,2nd_entry,3rd_entry
18/11/2021,This entry shows up on calendar,Not sure what this entry does but you need it
-</csv>-

Run it like this:
-----------------
python3 make-calendar.py 2021 cal-list.csv 0

Customization
-------------

You can change the calendar style in the file `head.tex.in`. Note that all
lengths and widths are predefined for DIN A4 paper. Month and day names will be
printed according to `LC_TIME` (or `LC_ALL` if `LC_TIME` is not set
separately).
