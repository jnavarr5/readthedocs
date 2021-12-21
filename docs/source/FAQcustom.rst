Custom Annotation Tracks
========================

Topics
------

-  `Displaying personal annotation data in the Genome
   Browser <#custom1>`__
-  `Adding a personal annotation track to the Genome Browser
   website <#custom2>`__
-  `Defining filter parameters for custom tracks <#custom3>`__
-  `Coloring a custom track using the useScore parameter <#custom4>`__
-  `Constructing a Genome Browser URL <#custom5>`__
-  `Using the hgsid parameter in a URL <#custom6>`__
-  `Creating a details page for a custom annotation track <#custom7>`__
-  `Custom annotation track troubleshooting <#custom8>`__
-  `Error 500: Internal server error <#custom9>`__
-  `Byte-range request error <#custom10>`__
-  `BedToBigBed and other utilities fail because of custom track header
   lines <#custom11>`__

--------------

`Return to FAQ Table of Contents <index.html>`__

Displaying personal annotation data in the Genome Browser
---------------------------------------------------------

How do I display my own personal annotation data in the Genome Browser?
                                                                       

To create an annotation track that will display on the Genome Browser,
you must first organize your data into a format supported by the browser
custom track feature: `GTF <FAQformat.html#format4>`__,
`GFF <FAQformat.html#format3>`__, `BED <FAQformat.html#format1>`__,
`WIG <FAQformat.html#format6>`__, or `PSL <FAQformat.html#format2>`__.
Then, upload your data into the Genome Browser on the `Add Custom
Tracks <../cgi-bin/hgCustom>`__ page. Once you've created your
annotation track, you can share it with others over the internet by
putting your annotation file on your website and then creating a custom
URL that allows others to directly start the browser with your track
displayed.

Read the `Creating custom annotation
tracks <../goldenPath/help/hgTracksHelp.html#CustomTracks>`__ section in
the Genome Browser User's Guide for a step-by-step description of how to
format and display a custom annotation track and create a custom URL.

Adding a personal annotation track to the Genome Browser website
----------------------------------------------------------------

I have an annotation track that I think might be of general interest to the research community. Will UCSC consider including my track in their browser?
                                                                                                                                                       

We are always interested in receiving new annotation tracks for the
Genome Browser, and encourage our users to share their tracks with us
and others in the research community. Please send the URL for your track
-- along with a description of the methods, data, and format used -- to
genome@soe.ucsc.edu. If we determine that your track is of sufficient
general interest to distribute as part of our browser, we'll work with
you to include it.

In addition to the standard set of tracks displayed on the Genome
Browser page, we also have a `Custom Annotation
Tracks <../goldenPath/customTracks/custTracks.html>`__ page that
contains contributed tracks we are unable to display in the main browser
(for example, tracks that are of too specific an interest or are too
sparse). We welcome contributions to this page.

Defining filter parameters for custom tracks
--------------------------------------------

Is it possible to define a filter parameter for a custom track to highlight certain features?
                                                                                             

This feature is not currently implemented.

Coloring a custom track using the useScore parameter
----------------------------------------------------

When designing a custom track, is there a way to assign specific colors to each segment, as is done in the mouse/rat synteny tracks? Is there a way to assign a value range for the *useScore* variable such that I can have four shades and specify the value range for each?
                                                                                                                                                                                                                                                                              

Currently *useScore* works only with tracks that are black or specific
shades of brown or blue. The score range is 0-1000. To display four
shades, use the scores 0, 333, 666, and 1000.

Constructing a Genome Browser URL
---------------------------------

How can I construct a URL to retrieve data from the Genome Browser? What do the various parameters in the Genome Browser URLs mean?
                                                                                                                                   

One way to determine how to construct a correct URL is to open a Genome
Browser link in which you are interested and examine how the Genome
Browser constructs the URL. See the `User's
Guide <../goldenPath/help/hgTracksHelp.html#CustomTracks>`__ for a
discussion of the basic components of a Genome Browser URL. Note that
the *c* parameter that appears in some URLs specifies the chromosome
name or the chromosome name and position.

Using the hgsid parameter in a URL
----------------------------------

Should I use the hgsid parameter in my URL?
                                           

Avoid using hgsid -- it is a temporary identifier, and will typically
stop working after a day.

Creating a details page for a custom annotation track
-----------------------------------------------------

While working on a custom track, we noticed that the feature details page for custom track looks different from regular tracks on the site. Is the details page for a custom track customizable?
                                                                                                                                                                                                

You can add a link from a details page to an external web page
containing additional information about the feature by using the track
line url attribute. In the annotation file, set the url attribute in the
track line to point to a publicly available page on a web server. The
url attribute substitutes each occurrence of '$$' in the URL string with
the name defined by the name attribute. You can take advantage of this
feature to provide individualized information for each feature in your
track by creating HTML anchors that correspond to the feature names in
your web page.

Custom annotation track troubleshooting
---------------------------------------

When I click the Submit button, I get the error message "line # of custom input: BED chromStarts[i] must be in ascending order".
                                                                                                                                

This error is caused by a logical conflict in the Genome Browser
software. It accepts custom GFF tracks that have multiple "exons" at the
same position, but not BED tracks that have this feature. Because the
browser translates GFF tracks to BED format before storing the custom
track data, GFF tracks with multiple exons will cause an error when the
BED is read back in. To work around this problem, remove duplicate lines
in the GFF track.

Error 500: Internal server error
--------------------------------

I'm getting an Error 500 when trying to upload my custom track(s). What am I doing wrong?
                                                                                         

This error may occur when trying to upload a file that is too large. For
larger data sets, we suggest using bigBed and bigWig file formats. More
information about selecting a format can be found
`here <http://genomewiki.ucsc.edu/index.php/Selecting_a_graphing_track_data_format>`__.

Byte-range request error
------------------------

When I try to visualize my custom track, I receive the error 'Byte-range request was ignored by server.
                                                                                                       

This error occurs when a web server is not configured properly or does
not support byte-ranges. Click
`here <../goldenPath/help/hgTracksHelp.html#BYTERANGE>`__ for more
information.

BedToBigBed and other utilities fail because of custom track header lines
-------------------------------------------------------------------------

Why does my custom track fail when I use ``bedToBigBed`` or utilities like ``validateFiles``?
                                                                                             

These utilities can fail when the input includes custom-track-specific
lines at the top of the file that are not considered part of the data.
Many of the custom track examples on the `File
Format <FAQformat.html>`__ page include a "``track  type=...``" line
that is specific for loading the data into the Browser. This line will
cause raw data files to fail validation by other tools, such as
``bedToBigBed`` or ``validateFiles``, outside of the Browser. To see an
example of using ``bedToBigBed`` with correct input data types, follow
this `link <../goldenPath/help/bigBed.html#Ex3>`__. More information
about track lines can be found
`here <../goldenPath/help/customTrack.html#TRACK>`__.
