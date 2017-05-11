# vexflow-syn
A synesthesic (relating to synesthesia) approach to coloring music notation in JavaScript by note.

## Purpose
The purpose of this is to create a new learning method for teaching musical notation to children, especially the very young. The hope would be that this approach will take advantage of neuroplasticity to actually promote synesthesia in the student. In my mind, recognizing the color combinations of piano chords could be made easier like this, making a C-maj chord more readily distinguishable from a D-maj, for example.

## Existing code

This projects builds on the excellent JavaScript library [vexflow](https://github.com/0xfe/vexflow) by 0xfe. See also [vexflow.com](http://www.vexflow.com) for more information and tutorials. To work with this project, you'd need some experience working with the way vexflow creates and decorates notation on one or more musical staves, as rendered to an HTML5 canvas.

## Definition

Wikipedia defines synesthesia as "a neurological phenomenon in which stimulation of one sensory or cognitive pathway leads to automatic, involuntary experiences in a second sensory or cognitive pathway".

In case you're interested, according to [this blog post](http://synspectrum.com/synesthesia.html), the synesthetic author experiences the following colors associated with these notes:

<table>
<tr><td>C:</td><td>white</td></tr>
<tr><td>C#/Db:</td><td>somewhat-metallic navy blue</td></tr>
<tr><td>D:</td><td>gray-green</td></tr>
<tr><td>D#:</td><td>yellow-green</td></tr>
<tr><td>Eb:</td><td>metallic gold</td></tr>
<tr><td>E:</td><td>bright yellow</td></tr>
<tr><td>F:</td><td>crimson red, tending toward magenta (very vivid and rich)</td></tr>
<tr><td>F#:</td><td>maroon, a bit redder</td></tr>
<tr><td>Gb:</td><td>metallic maroon, slightly darker</td></tr>
<tr><td>G:</td><td>brown-orange, browner the lower the note is</td></tr>
<tr><td>G#:</td><td>bright/matte-finish orange-copper</td></tr>
<tr><td>Ab:</td><td>metallic copper/brass</td></tr>
<tr><td>A:</td><td>orange</td></tr>
<tr><td>A#:</td><td>magenta</td></tr>
<tr><td>Bb:</td><td>beautiful royal purple--more violet, reddish-purple hue</td></tr>
<tr><td>B:</td><td>a very crisp black</td></tr>
</table>

## Synesthetes
Alexander Scriabin (1872-1915), Hélène Grimaud (1969-), Franz Liszt (1811-1886), Itzhak Perman (1945-), Duke Ellington (1899-1974, Joachim Raff (1822-1882), Jean Sibelius (1865-1957), György Ligeti (1923-2006), Nikolai Rimsky-Korsakov (1844-1908), Olivier Messiaen (1908-1992) and David Hockney (1937) all were famous musicians and composers who wrote about their own synesthesia and how it affected them personally.

## A strategy for coloring notation
Since I've not been able to determine a commonality or consensus among the anecdotal collective evidence of existing writings, I've decided to issue colors based upon a common childhood toy from kindergarten:  the xylophone. 

![xylophone](https://cloud.githubusercontent.com/assets/15971213/25959487/95def22e-3628-11e7-9a7e-022278aeb1a8.jpg)

The approach here is to use the natural red-to-violet color spectrum and map this to the span of one octave of white keys on a typical piano keyboard. This gives us the following table:

<table>
<tr><td>C</td><td>red</td></tr>
<tr><td>D</td><td>orange</td></tr>
<tr><td>E</td><td>yellow</td></tr>
<tr><td>F</td><td>green</td></tr>
<tr><td>G</td><td>blue</td></tr>
<tr><td>A</td><td>purple</td></tr>
<tr><td>B</td><td>violet</td></tr>
</table>

Next, we need to find a color for the accidentals (sharps/flats). The best method here appears to be to find an intermediate color between the notes above/below and then I've decided to make the color grayer, more pastel in feel.

![example](https://cloud.githubusercontent.com/assets/15971213/25960561/2750f948-362c-11e7-9eaf-d5ca4206393d.png)

In this example, we see a chromatic scale in the first stave: B, C, C#, D | Eb, E, F, F# | G, G#, A and a rest.  The next stave includes: Bb, B, C, C# | D, Eb, E, F | F#, G, G# and A.  The final stave includes four major chords (C-maj, D-maj, E-maj and F-maj) followed by their minors (C-min, D-min, E-min and F-min).

One should readily see some of the advantages here with the colorized version:
* Visualizing octaves on the piano would be monochromatic, there might be two red notes separated by a common distance across the stave, for example.
* All black keys on the piano appear grayer in color than their white-key counterparts.
* The red/yellow/blue primary color combination is seen in the C-maj 1-3-5 chord.  If the expected yellow middle note is shifted more orange and grayer, then this is a quick visual indication of the C-min variation in this case.
* A melody which is gradually moving through the color spectrum is chromatic (half-note steps).  A melody which is in a major key like C-maj has little gray in it. 
* In musical theory for conventional music, you often hear terms like "dominant" (for the C-maj key that's 5-7-9 or G/B/D or blue/violet/orange in this case).  So the music might begin with the root C-maj red/yellow/blue, then move to the dominant G-maj blue/violet/orange, temporarily move to the fourth F-maj with green/purple/red and then back to the root. With practice, the recognition of these color movements could make things easier for the student, if not almost instinctual at some point.

## Progress
At the moment, this project is simply an example of a client-side approach to displaying a few staves of colorized musical notation.  It relies upon the (normally external) dependency of the vexflow JavaScript include but to make things easier I've copied a snapshot of this library to make installation go quickly for you.

## Installation
```
$ git clone https://github.com/OutsourcedGuru/vexflow-syn.git
$ cd vexflow-syn
$ open index.html         // in theWindows, "start index.html"
```

## Notes
It looks like vexflow at the moment is a little early in its development cycle. Although it's an awesome effort by its author, it still lacks in the ease-of-use areas, in my humble opinion.  You might also want to investigate some of the one-off projects like https://github.com/rubiety/vexflow-json and https://github.com/rubiety/jquery-vexflow-json which likely make things easier on importing into the note array for one or more staves.

What appears to be missing is "stave continuation" (for want of a term to describe it), a feature which would allow an entire score to be added as a single array.  In theory, then, the rendering engine would make some reasonable assumptions about note spacing and then essentially do what any text editor might: find suitable places to add an end-of-line character to move to the next line (stave), in this case.  The underlying vexflow library does not have this.

I'm also in the learning stage for vexflow since this project is less than a week old for me, to be honest.  I find it difficult at the moment to easily change note durations without this causing errors in the rendering step.  It feels like the vexflow author expects me to manually type in the beat count for each stave but I'd rather do this programmatically, of course.
