kanten
======
Japanese for word for agar, a gelatinous substance derived from seaweed.

This program was inspired by a similar one called [Tofu][] for OS X, a
column-based reader application, where the columns are arranged horizontally.
Given the aspect ratio of computer monitors, I decided to create kanten to be a
unix pager replacement (more and less) that is not limited to 80 columns.

possible other names
--------------------
onte - [c]onte[xt] [c]onte[nt]
kinc - "A little more than kin, and less than kind"
bond - "according to my bond, no more, nor less"

TODO
----
[x] horizontal progress bar indicator
[x] figure out how many columns are displayed, and adjust pbar accordingly
[x] don't make the last displayed columns disappear at the end?
[x] (n / m) total pages (columns) indicator
[x] some vertical empty space at the top
[x] space bar should move one column over (or whole screen?)
[x] reading from stdin
[x] process keyboard shortcuts after reading from stdin (the way less does)
[ ] read buffering (don't read the whole file before filling in)
[x] specifying a filename from commandline
[ ] demo file that explains kanten (tutorial)
[ ] do a full install as a python package with an entry point
[ ] configuration in ~/.config/kanten
[ ] all configurable take defaults from ~/.config, but overwritten by params
[x] configurable number of columns (via -w or --width)
[x] automatically figure out size (for height, and number of columns)
[ ] 'v' to edit the file (disabled for stdin?)
[ ] open file to the right line (at least the top-left column's line
[ ] on exit, refresh the file in kanten
[ ] run_wrapper to restore previous screen?
[ ] dynamic resizing of width
[x] param parsing (e.g. add --help)
[ ] hide the progress bar (ctrl-n is what zathura uses or something?)
[ ] add a parameter to disable progress bar
[ ] add help dialog on ? and possibly h
[ ] add : command mode
    - support :q
    - support :f for file info
[ ] (maybe) support multiple buffers?
    - :n and :p (or :N) for next and previous
    - :e to read a different file?
[x] . (dot) to repeat previous command (page up or down, next, etc)
[ ] support more less/more keys 
    [x] < and >
    [x] z and w
    [x] j and k (page-wise OK)
    [x] = to show file name / info (ctrl-g should also work)
    [ ] others?
    [ ] F - forward forever (for stdin)
[ ] control key combos
    [x] ctrl-v  ctrl-f  for page forward and ctrl-b for back back
    [x] ctrl-g for file info
[ ] (maybe) implement marking system (top lines?)
    - like less, marks will only live for duration of program execution
[ ] (maybe) support 'v' to edit, like less
    - wouldn't support editing stdin, just like less
[ ] support jumping to a particular line
    - would go along with editing a file at that line
    - and allow us to jump back into the same line after editing?
[ ] support ctrl-i and ctrl-o location-list jumping
[x] reflow of text
[ ] (maybe) reading cursor (like dictator?)
[x] 'g' to go to the beginning 
[x] 'G' to go to the end
[x] split boxes so that they partially fit
[x] clip off lines that are too long even in one go
[x] last line of text being cut-off
[x] fix formatting (spacing) for cells which were cut
[x] columns currently allowed to expand: don't let them 
    - boxadapter?
    - options('given', width) ?
    - use padding!!
[ ] (alignment) 'the less is' line currently getting screwed up :\
[ ] (refactor) start off with one Padding(text) and keep splitting in
    - don't pre-split
    - such an approach will be a reasonable way to go with searching, anyway
        - i.e. highlight the word in every instance, and reflow?
        - or at least to find the location of the word, and then index into the
          right / approximate column
    - also makes it reasonable to scroll line by line (daisy chain visible cols)
    - stop after all visible columns are filled
[ ] search using / (to seek around)
[ ] highlight words in the text
[ ] highlight searched word (switch to ANSIText?) 
[ ] replace searched words with highlighted version
[ ] wrap-around optionally
[x] going forward 4 times and then going back 4 doesn't work :(
    maybe related:
        File "/usr/lib/python2.7/dist-packages/urwid/widget.py", line 142, in cached_render validate_size(self, size, canv)
        File "/usr/lib/python2.7/dist-packages/urwid/widget.py", line 112, in validate_size canv.rows(), size))
        urwid.widget.WidgetError: Widget <Filler box widget <Columns box/flow widget> valign='top'> rendered (193 x 45) canvas when passed size (193, 51
    [x] (maybe) try cache invalidation? nope, _invalidate doesn't hel
    [x] [cols.focus_position=0 seems to have done the trick!
