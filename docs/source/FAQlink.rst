Linking to the Genome Browser
=============================

Topics
------

.. container:: row

   .. container:: col-md-5

      .. rubric:: `Creating a sharable URL to view specific
         tracks <#link1>`__
         :name: creating-a-sharable-url-to-view-specific-tracks

      .. rubric:: `Linking to the Browser at a specific position, or
         default position <#link2>`__
         :name: linking-to-the-browser-at-a-specific-position-or-default-position

      .. rubric:: `Zooming in or out using a link to an HGVS
         identifier <#zoomVariant>`__
         :name: zooming-in-or-out-using-a-link-to-an-hgvs-identifier

      .. rubric:: `Setting track visibility via URL <#trackViz>`__
         :name: setting-track-visibility-via-url

      .. rubric:: `Loading Custom Tracks with the URL <#custUrl>`__
         :name: loading-custom-tracks-with-the-url

      .. rubric:: `Loading Track Hubs and Assembly Hubs with the
         URL <#hubUrl>`__
         :name: loading-track-hubs-and-assembly-hubs-with-the-url

      .. rubric:: `Linking to gene-specific information <#genes>`__
         :name: linking-to-gene-specific-information

      .. rubric:: `The hgsid parameter <#hgsid>`__
         :name: the-hgsid-parameter

      .. rubric:: `Additional URL parameters <#moreInfo>`__
         :name: additional-url-parameters

      .. rubric:: `Video demonstrations of making links <#Videos>`__
         :name: video-demonstrations-of-making-links

      -  `Understanding the URL <#LinkVid1>`__
      -  `Jump into genes <#LinkVid2>`__
      -  `Composites, custom tracks, spreadsheets <#LinkVid3>`__

   .. container:: col-md-7

      Search the Genome Browser help pages:  

      `Questions and feedback are welcome <../../contacts.html>`__.

.. _creating-a-sharable-url-to-view-specific-tracks-1:

Creating a sharable URL to view specific tracks
-----------------------------------------------

How do I create a link to the Genome Browser to share my data?
                                                              

The easiest way to save and share tracks from the URL is by `logging
in <../cgi-bin/hgLogin>`__ to your Genome Browser account and creating a
`saved session <../goldenPath/help/hgSessionHelp.html>`__. Saved
sessions are a versatile way to share data that may include native
annotations, Custom Tracks, Track Hubs, and Assembly Hubs. In these
examples, text in brackets **"<"** and **">"** indicate places where the
user supplies information. Note that the brackets are not needed for the
URL, including the brackets will result in a 'Could not find session'
error.

You will be able to share Genome Browser sessions with the following
link format:

``http://genome.ucsc.edu/s/<userName>/<sessionName>``

For instructions on creating a saved session, go to the `session user
guide <../goldenPath/help/hgSessionHelp.html#Create>`__. If you want to
specify track settings in a URL directly, please read the section on
`setting track visibility via URL <#trackViz>`__ for a complete
description.

Or if you prefer the older style, which allows you to link to different
tools, you may use the following format:

``http://genome.ucsc.edu/cgi-bin/hgTracks?hgS_doOtherUser=submit&hgS_otherUserName=<userName>&gS_otherUserSessionName=<sessionName>``

This longer format has the flexibility of replacing "hgTracks" with
different tool names to share saved settings on the Table Browser
(hgTables), Variant Annotation Integrator (hgVai), or Data Integrator
(hgIntegrator). This will preserve your option selections and can be
useful to share. The following format will bring the recipient to a
user's custom Table Browser selections:

``http://genome.ucsc.edu/cgi-bin/hgTables?hgS_doOtherUser=submit&hgS_otherUserName=<userName>&hgS_otherUserSessionName=<sessionName>``

Both session link formats have the advantage of being able to add URL
parameters to the end. The shorter link format requires a question mark
before any URL parameters, with ampersand characters separating
different parameters like so:

``http://genome.ucsc.edu/s/view/clinicalzoom?textSize=18``

Both formats require an ampersand between each additional parameter,
seen in the longer format like so:

``http://genome.ucsc.edu/cgi-bin/hgTracks?hgS_doOtherUser=submit&hgS_otherUserName=view&hgS_otherUserSessionName=clinicalzoom&textSize=18``

.. _linking-to-the-browser-at-a-specific-position-or-default-position-1:

Linking to the Browser at a specific position, or default position
------------------------------------------------------------------

How do I make a link to a specific genome, position, or HGVS variant?
                                                                     

You can link to a specific genome assembly and position in the Genome
Browser using a URL with the ``db=`` and ``position=`` parameters.

``http://genome.ucsc.edu/cgi-bin/hgTracks?db=<assembly>&position=<position>``

Where:

-  ``db`` - designates a specific genome assembly. For example,
   ``db=hg19`` refers to the Feb. 2009 human genome release. For a list
   of db parameter values that correspond to UCSC assemblies, see the
   `list of UCSC releases <FAQreleases.html#release1>`__.
-  ``position`` - can be any search term for the genome specified,
   including a position range or a gene identifier. This often takes the
   form of ``position=chr1:35000-40000``.

The following link is an example of a URL that declares assembly and
position:

``http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg19&position=chr1:35000-40000``

How do I make a link to the default position of a genome?
                                                         

You can link directly to the default position of an assembly by passing
the ``position=default`` parameter. This can be helpful in cases where a
track exists on multiple assemblies, and you want to build links to each
of them. If no position variable is passed, the Genome Browser assumes
the default position for the default assembly (hg38).

Here is an example which opens the uniprot track at the default position
for sacCer3:

``http://genome.ucsc.edu/cgi-bin/hgTrackUi?db=sacCer3&g=uniprot&position=default``

Zooming in or out with a link — HGVS
------------------------------------

How do I zoom out using a link to a HGVS identifier?
                                                    

To link to a specific HGVS identifier, you can construct a link with the
HGVS identifier in the position field instead of coordinates. The
default padding is 5bp on either side, but you can always zoom in or out
with ``hgt.out1=submit`` or ``hgt.in1=submit``. The numbers 1 through 4
zoom in or out corresponding to the buttons above the track window. The
following lists the zoom levels of each number, applicable to zooming in
or out:

-  ``hgt.out1=submit`` zooms out 1.5x
-  ``hgt.out2=submit`` zooms out 3x
-  ``hgt.out3=submit`` zooms out 10x
-  ``hgt.out4=submit`` zooms out 100x

The following link is an example which leads to the variant
NM_00257:c.1208G>T and zooms out 3x:

``http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg19&position=NM_000257:c.1208G>T&hgt.out2=submit``

.. _setting-track-visibility-via-url-1:

Setting Track Visibility via URL
--------------------------------

How do I create a custom URL to control the visibility of specific tracks?
                                                                          

You can control the visibility of tracks from the URL with the following
parameters, each linked by the "&" sign, similar to position parameters.
For more information, please see the `optional URL
parameters <../goldenPath/help/customTrack.html#optParams>`__ section of
the Custom Tracks User's Guide.

-  ``hideTracks=1`` - hides all tracks
-  ``<trackName>=hide|dense|pack|full`` - sets specified track or
   subtrack to a chosen visibility
-  ``textSize=<number>`` - sets browser text size to either 6, 8, 10,
   12, 14, 18, 24, or 34. Default is a textSize of 12.
-  ``<trackName>.heightPer=<###>`` - sets a bigWig track's height to a
   particular number of pixels (between 20-100)
-  ``ignoreCookie=1`` - removes pre-existing user settings like track
   selection, custom tracks, and track hubs

For example, you can use the following command to hide every track
(hideTracks=1), set the genome database to hg38 (db=hg38), set the
mappability track to full visibility (mappability=full), and set the
umap track height to 100 pixels (umap24Quantitative.heightPer=100). Each
of these parameters can be used individually or in combination.

``http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&hideTracks=1&mappability=full&umap24Quantitative.heightPer=100``

Composite tracks have additional URL parameters that encode options to
hide, select, and display subtracks.

-  ``<trackName>_hideKids=1`` - hides a specific composite track's
   subtracks
-  ``<trackName>_sel=1`` - selects specific subtrack to be 'checked',
   allowing display

For example, the following URL hides all tracks (hideTracks=1), hides a
specific composite track's default subtracks
(refSeqComposite_hideKids=1), turns on one specific subtrack
(ncbiRefSeqCurated=full), and checks a box to display that subtrack
(ncbiRefSeqCurated_sel=1).

::

   https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&hideTracks=1&refSeqComposite_hideKids=1&ncbiRefSeqCurated=full&ncbiRefSeqCurated_sel=1

Loading data with the URL
-------------------------

Loading Custom Track data with the URL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How do I create a link to my custom track data?
                                               

If you have a custom track on a web-accessible server, you can use the
location of the file to load it directly as part of a URL. You can
combine the URL visibility settings with the ``hgct_customText=``
parameter using a track line you would otherwise put in the `custom
track input box <../cgi-bin/hgCustom>`__. The following example shows
the ``hgct_customText`` parameter accepting a bigBed file URL as a
custom track:

::

   http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&position=chr21:34821279-34888690&hgct_customText=https://genome.ucsc.edu/goldenPath/help/examples/bigBedExample.bb

If you want to add more information to the Custom Track, you can do so
using the ``hgct_customText`` parameter. Since this is a URL, you must
use "%20" to encode for spaces and "%0A" for a new line character. For
example, the following example shows Custom Track input pasted in the
`custom track input box <../cgi-bin/hgCustom>`__ and the equivalent
input in the URL:

::

   browser position chr21:33038946-33039092
   track type=bam bigDataUrl=https://genome.ucsc.edu/goldenPath/help/examples/bamExample.bam name=Example description=ExampleBAM

::

   http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg38&hgct_customText=browser%20position%20chr21:33038946-33039092%0Atrack%20type=bam%20bigDataUrl=https://genome.ucsc.edu/goldenPath/help/examples/bamExample.bam%20name=Example%20description=ExampleBAM

More information on custom track parameters can be found in the `Custom
Track user guide <../goldenPath/help/customTrack.html>`__.

.. _loading-track-hubs-and-assembly-hubs-with-the-url-1:

Loading Track Hubs and Assembly Hubs with the URL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

How do I create a link to my track hub or assembly hub?
                                                       

Similar to custom tracks, track hubs can be loaded into the URL using
the ``hubUrl=`` parameter. This parameter takes input similar to the
`track hub input box <../cgi-bin/hgHubConnect#unlistedHubs>`__. The
following example links to the hg19 genome database and an example track
Hub:

::

   http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg19&hubUrl=https://genome.ucsc.edu/goldenPath/help/examples/hubDirectory/hub.txt

Track hubs' track visibility can also be changed from the URL
parameters. The following link specifies the genome database (db=hg19),
loads a track hub (hubUrl=http.../hub.txt), hides all tracks
(hideTracks=1), hides the subtrack kids of a particular track
(gtexRnaSignalMaleYoung_hideKids=1), sets a specific subtrack to be
displayed (gtexRnaSignalSRR1311243=full), and ignores user settings
(ignoreCookie=1).

::

   https://genome.ucsc.edu/cgi-bin/hgTracks?db=hg19&hubUrl=http://hgdownload.soe.ucsc.edu/hubs/gtex/hub.txt&hideTracks=1&gtexRnaSignalMaleYoung_hideKids=1&gtexRnaSignalMaleYoung=full&gtexRnaSignalSRR1311243=full&ignoreCookie=1

To link to an assembly hub and display data on a non-natively supported
genome, the same parameters apply. To specify the intended genome
assembly, instead of using ``db=``, you must use ``genome=araTha1``,
where araTha1 is the assembly name set by your genomes.txt file in the
line ``genome araTha1``.

::

   https://genome.ucsc.edu/cgi-bin/hgTracks?genome=araTha1&hubUrl=http://genome.ucsc.edu/goldenPath/help/examples/hubExamples/hubAssembly/plantAraTha1/hub.txt

To see the files behind that assembly hub, please visit the `hub's
directory <../goldenPath/help/examples/hubExamples/hubAssembly/plantAraTha1/>`__.
For more information on assembly hubs in general, please see the
`assembly hub
wiki <http://genomewiki.ucsc.edu/index.php/Assembly_Hubs>`__, the `track
hub user guide <../goldenPath/help/hgTrackHubHelp.html>`__, or the
`quick start guide to assembly
hubs <../goldenPath/help/hubQuickStartAssembly.html>`__.

.. _linking-to-gene-specific-information-1:

Linking to gene-specific information
------------------------------------

How do I link to a specific gene or specific gene description page?
                                                                   

To jump directly to a gene's position on the Genome Browser, set the
position parameter in the URL to a gene symbol (e.g., TP53, MTOR, KRAS)
and add the parameter ``singleSearch=knownCanonical``. For example, the
following link will open the Genome Browser for the hg19 human assembly
at the position of TP53 on the knownCanonical dataset

``http://genome.ucsc.edu/cgi-bin/hgTracks?db=hg19&singleSearch=knownCanonical&position=TP53``

You can also link directly to gene description pages from the URL.
Instead of a position search, gene descriptions use the ``hgg_gene=``
URL parameter. The following URL connecting to 'hgGene' will open up the
Genome Browser description page containing protein function, expression
profile, and links to additional information for the gene TP53.

``http://genome.ucsc.edu/cgi-bin/hgGene?db=hg19&hgg_gene=TP53``

.. _the-hgsid-parameter-1:

The *hgsid* parameter
---------------------

What is the hgsid parameter and should I include it in Genome Browser links?
                                                                            

The hgsid is a temporary user ID that stores setting and custom track
information in the URL. Including it in any shared URLs is a privacy
concern, and it should be removed when constructing any links to the
Genome Browser. Most significantly, it will change after you share it.
Anyone using it will see that last thing you did, not what you thought
you were sharing. Creating `Saved
Sessions <../goldenPath/help/hgSessionHelp.html#Create>`__ is the
recommended way to share Genome Browser information.

.. _additional-url-parameters-1:

Additional URL parameters
-------------------------

Are there any more resources for URL and link parameters?
                                                         

For more information, please see our `section on URL parameters for
custom tracks <../goldenPath/help/customTrack.html#optParams>`__. If you
cannot find what you are looking for, please contact our active mailing
list by emailing
`genome@soe.ucsc.edu <mailto:genome@soe.ucsc.%0Aedu>`__. All messages
sent to that address are publicly archived. If your question includes
sensitive data, you may send it instead to `genome-www@soe.
ucsc.edu <mailto:genome-www%0A@soe.ucsc.edu>`__

Videos
------

Video demonstration: Links: Understanding the URL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Visit our `YouTube
channel <https://www.youtube.com/channel/UCQnUJepyNOw0p8s2otX4RYQ/videos>`__.

Video demonstration: Links: Jump into genes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Visit our `YouTube
channel <https://www.youtube.com/channel/UCQnUJepyNOw0p8s2otX4RYQ/videos>`__.

| 

Video demonstration: Links: Composites, custom tracks, spreadsheets
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

| 

      Visit our `YouTube
channel <https://www.youtube.com/channel/UCQnUJepyNOw0p8s2otX4RYQ/videos>`__.
