# Python Chord Diagram Generator

**Original work by joebrown.org.uk, (C) 2011, 2012**, which he based on *'Draw
Guitar Chords using PHP'* by Tony Pottier, and his own PHP SVG Chord Generator.

I found this online, and the code was a little alpha, so I decided to refactor
to be a bit cleaner and more useable.  Refactoring work is still ongoing.
Original was tagged as V2.10, however I'm retagging using `semver` and will
place this as `<1.0` version until I'm happy with the class and structure.

## Todo

-   Configuration of plot styling (scaling, colour, output fmt)
    -   Function-based or CSS?
-   Modification of generator to functional style (don't really need to maintain
    multiple chords, so don't need state-based class)
-   Use a string template for the output SVG, rather than repeated writes?
-   Quick (command line) generation...just give 6 notes, and optional name
-   Generate poster showing common/nice voicings for each key

## Usage

To generate svg files of the name `chordname.svg` in the current directory, run
the following:

```python
from chordGen import chord

chords=[
    {"name":'A5', "notes":['X',0,2,2,'x','x'],"comment":"Power Chord"},
    {"name":'A7sus4', "notes":['X',0,2,0,3,0]},
    {"name":'A', "notes":[5,7,7,6,5,5],"comment":"Barre chord"},
    {"name":'A', "notes":[5,7,7,6,5,5],"capo":2},
    {"name":'B', "notes":['X','X',4,4,4,7],"cut":3,"comment":"Partial B"}
]

with open("Chords.html",'w') as f:
    f.write("<table>")
    for val in chords:
        f.write("<tr><td><img src='{}.svg'/></td></tr>".format(val['name']))
        chord(**val).draw()
    f.write("</table>")
```

![Example A5 diagram](./A5.svg)
