Frequently Asked Questions: BLAT
================================

Topics
------

-  `BLAT vs. BLAST <#blat1>`__
-  `BLAT cannot find a sequence at all or not all expected
   matches <#blat1b>`__
-  `BLAT or In-Silico PCR finds multiple matches such as chr_alt or
   chr_fix even though only one is expected <#blat1c>`__
-  `BLAT use restrictions <#blat2>`__
-  `Downloading BLAT source and documentation <#blat3>`__
-  `Replicating web-based BLAT parameters in command-line
   version <#blat5>`__
-  `Using the -ooc flag <#blat6>`__
-  `Replicating web-based BLAT percent identity and score
   calculations <#blat4>`__
-  `Replicating web-based BLAT "I'm feeling lucky" search
   results <#blat7>`__
-  `Using BLAT for short sequences with maximum sensitivity <#blat8>`__
-  `BLAT ALL genomes <#blat9>`__
-  `BLAT ALL genomes: No matches found <#blat10>`__
-  `Approximating web-based BLAT results using
   gfServer/gfClient <#blat11>`__
-  `Standalone or gfServer/gfClient result start positions off by
   one <#blat12>`__
-  `Protein-translated BLAT having different results <#blat13>`__

--------------

`Return to FAQ Table of Contents <index.html>`__

BLAT vs. BLAST
--------------

What are the differences between BLAT and BLAST?
                                                

BLAT is an alignment tool like BLAST, but it is structured differently.
On DNA, BLAT works by keeping an index of an entire genome in memory.
Thus, the target database of BLAT is not a set of GenBank sequences, but
instead an index derived from the assembly of the entire genome. By
default, the index consists of all non-overlapping 11-mers except for
those heavily involved in repeats, and it uses less than a gigabyte of
RAM. This smaller size means that BLAT is far more easily
`mirrored <../goldenPath/help/mirror.html>`__ than BLAST. Blat of DNA is
designed to quickly find sequences of 95% and greater similarity of
length 40 bases or more. It may miss more divergent or shorter sequence
alignments. (The default settings and expected behavior of standalone
Blat are slightly different from those on the `graphical version of
BLAT <../cgi-bin/hgBlat>`__.)

On proteins, BLAT uses 4-mers rather than 11-mers, finding protein
sequences of 80% and greater similarity to the query of length 20+ amino
acids. The protein index requires slightly more than 2 gigabytes of RAM.
In practice -- due to sequence divergence rates over evolutionary time
-- DNA BLAT works well within humans and primates, while protein Blat
continues to find good matches within terrestrial vertebrates and even
earlier organisms for conserved proteins. Within humans, protein Blat
gives a much better picture of gene families (paralogs) than DNA Blat.
However, BLAST and psi-BLAST at NCBI can find much more remote matches.

From a practical standpoint, BLAT has several advantages over BLAST:

-  speed (no queues, response in seconds) at the price of lesser
   homology depth
-  the ability to submit a long list of simultaneous queries in fasta
   format
-  five convenient output sort options
-  a direct link into the UCSC browser
-  alignment block details in natural genomic order
-  an option to launch the alignment later as part of a custom track

BLAT is commonly used to look up the location of a sequence in the
genome or determine the exon structure of an mRNA, but expert users can
run large batch jobs and make internal parameter sensitivity changes by
installing command-line Blat on their own Linux server.

BLAT can't find a sequence or not all expected matches
------------------------------------------------------

I can't find a sequence with BLAT although I'm sure it is in the genome. Am I doing something wrong?
                                                                                                    

First, check if you are using the correct version of the genome. For
example, two versions of the human genome are currently in wide use
(hg19 and hg38) and your sequence may be only in one of them. Many
published articles do not specify the assembly version so trying both
may be necessary.

Very short sequences that go over a splice site in a cDNA sequence can't
be found, as they are not in the genome. qPCR primers are a typical
example. For these cases, try using `In-Silico PCR <../cgi-bin/hgPcr>`__
and selecting a gene set as the target. In general, the In-Silico PCR
tool is more sensitive and should be preferred for pairs of primers.

Another problematic case is searching for sequences in repeats or
transposons. BLAT skips the most repetitive parts of the query and
limits the number of matches it finds, leading to missing matches for
these repeat sequences. The online version of BLAT masks 11mers from the
query that occur more than 1024 times in the genome and limits results
to 16 matches per chromosome strand. This means that at most 32
locations per chromosome are returned. This is done to improve speed,
but can result in missed hits when you are searching for sequences in
repeats.

Often for repeat sequences, you can use the `self-chain
track <../cgi-bin/hgTrackUi?db=hg38&g=chainSelf>`__ to find the other
matches, but only if the other matches are long and specific enough. You
can check whether any sequence is present at a particular location by
using the `"Short match"
track <../cgi-bin/hgTrackUi?db=hg38&g=oligoMatch>`__ if your sequence is
less than 30 bp. You can work around this minimum length limitation by
adding more flanking sequence to your query to make the query unique
enough. If this is not possible, the only alternative is to download the
executables of BLAT and the .2bit file of a genome to your own machine
and use BLAT on the command line. See `Downloading BLAT source and
documentation <#blat3>`__ for more information. When using the command
line version of BLAT, you can set the repMatch option to a large value
to try to improve finding matches in repetitive regions and do not use
one of the default 11.ooc repeat masking files.

BLAT or In-Silico PCR finds multiple matches such as chr_alt or chr_fix even though only one is expected
--------------------------------------------------------------------------------------------------------

I am seeing two or more matches in the genome although there should only be one. What are these extra matches?
                                                                                                              

This usually occurs on the newer genome assmeblies, such as hg38, when
you search a sequence that has an "alternate" or "fix" sequence. To
improve the quality of the these assemblies, curators have added
multiple versions of some important loci, e.g. the MHC regions. They
also add fix sequences to resolve errors without changing the reference.
See our `patches blog post <http://genome.ucsc.edu/blog/patches/>`__ for
more information.

When you blat or isPCR a sequence which matches a chromosome location
that also has a fix or alt sequence, you will see a match on the
reference chromosome (e.g. "chr1") and another match on the patch
sequence (e.g. chr1_KN196472v1_fix). In most cases it is safe to ignore
the patch hit, as a human genome will not contain both the reference and
alternate sequence at the same time. For more information on the
specific kinds of patch sequences see our `FAQ
entry <FAQdownloads#downloadAlt>`__ on the topic.

BLAT usage restrictions
-----------------------

I received a warning from your Blat server informing me that I had exceeded the server use limitations. Can you give me information on the UCSC Blat server use parameters?
                                                                                                                                                                           

Due to the high demand on our Blat servers, we restrict service for
users who programmatically query the BLAT tool or do large batch
queries. Program-driven use of BLAT is limited to a maximum of one hit
every 15 seconds and no more than 5,000 hits per day. Please limit batch
queries to 25 sequences or less.

For users with high-volume Blat demands, we recommend downloading the
BLAT tool for local use. For more information, see `Downloading BLAT
source and documentation <#blat3>`__.

Downloading BLAT source and documentation
-----------------------------------------

Is the BLAT source available for download? Is documentation available?
                                                                      

BLAT source and executables are freely available for academic, nonprofit
and personal use. Commercial licensing information is available on the
`Kent Informatics website <http://www.kentinformatics.com>`__.

BLAT source may be downloaded from http://hgdownload.soe.ucsc.edu/admin/
(located at /kent/src/blat within the most recent jksrci*.zip source
tree). For BLAT executables, go to
http://hgdownload.soe.ucsc.edu/admin/exe/ and choose your machine type.

Documentation on BLAT program specifications is available
`here <../goldenPath/help/blatSpec.html>`__. Note that the command-line
BLAT does not return matches to U nucleotides in the query sequence.

Replicating web-based Blat parameters in command-line version
-------------------------------------------------------------

I'm setting up my own Blat server and would like to use the same parameter values that the UCSC web-based Blat server uses.
                                                                                                                           

We almost always **expect small differences** between the
hgBLAT/gfServer and the stand-alone, command-line Blat. The best matches
can be found using pslReps and pslCDnaFilter utilities. The web-based
Blat is tuned permissively with a minimum cut-off score of 20, which
will display most of the alignments. We advise deciding which filtering
parameters make the most sense for the experiment or analysis. Often
these settings will be different and more stringent than those of the
web-based Blat. With that in mind, use the following settings to
approximate the search results of the web-based Blat:

**Note:** There are cases where the gfServer/gfClient approach provide a
better approximation of web results than standalone Blat. See the
`example below <#blat11>`__ for an overview of this process.

*standalone Blat*:

-  Blat search:
      ``blat -stepSize=5 -repMatch=2253 -minScore=20 -minIdentity=0   database.2bit query.fa output.psl``
-  **Note:** To replicate web results, PSL output should be used. BLAT
   handles alternative output formats (such as blast8) slightly
   differently, and this can lead to minor differences in results;
   particularly for short alignments. Furthermore, the query sequence
   should have all U nucleotides converted to T nucleotides or have the
   "-q=rna" flag used to match the web-BLAT.

*faToTwoBit*:

-  Uses soft masking to convert Fasta format to the 2bit format for BLAT
   input.

*gfServer* (this is how the UCSC web-based BLAT servers are configured):

-  BLAT server (capable of PCR):
      ``gfServer start blatMachine portX -stepSize=5 -log=untrans.log    database.2bit``
-  translated BLAT server:
      ``gfServer start blatMachine portY -trans -mask -log=trans.log    database.2bit``

For enabling DNA/DNA and DNA/RNA matches, only the host, port and twoBit
files are needed. The same port is used for both untranslated Blat
(gfClient) and PCR (webPcr). You'll need a separate Blat server on a
separate port to enable translated Blat (protein searches or translated
searches in protein-space).

*gfClient*:

-  Set *-minScore=0* and *-minIdentity=0*. This will result in some
   low-scoring, generally spurious hits, but for interactive use it's
   sufficiently easy to ignore them (because results are sorted by
   score) and sometimes the low-scoring hits come in handy.

Notes on repMatch:

-  The default setting for gfServer dna matches is: repMatch = 1024 \*
   (tileSize/stepSize).
-  The default setting for Blat dna matches is: repMatch = 1024 (if
   tileSize=11).
-  To get command-line results that are equivalent to web-based results,
   repMatch must be specified when using BLAT.

For more information about how to replicate the score and percent
identity matches displayed by our web-based Blat, please see this `BLAT
FAQ <../FAQ/FAQblat.html#blat4>`__.

For more information on the parameters available for BLAT, gfServer, and
gfClient, see the `BLAT
specifications <../goldenPath/help/blatSpec.html>`__.

Using the *-ooc* flag
---------------------

What does the *-ooc* flag do?
                             

Using any *-ooc* option in BLAT, such as *-ooc=11.ooc*, speeds up
searches similar to repeat-masking sequence. The *11.ooc* file contains
sequences determined to be over-represented in the genome sequence. To
improve search speed, these sequences are not used when seeding an
alignment against the genome. For reasonably sized sequences, this will
not create a problem and will significantly reduce processing time.

By not using the *11.ooc* file, you will increase alignment time, but
will also slightly increase sensitivity. This may be important if you
are aligning shorter sequences or sequences of poor quality. For
example, if a particular sequence consists primarily of sequences in the
*11.ooc* file, it will never be seeded correctly for an alignment if the
*-ooc* flag is used.

In summary, if you are not finding certain sequences and can afford the
extra processing time, you may want to run BLAT without the *11.ooc*
file if your particular situation warrants its use.

Replicating web-based Blat percent identity and score calculations
------------------------------------------------------------------

Using my own command-line Blat server, how can I replicate the percent identity and score calculations produced by web-based Blat?
                                                                                                                                  

There is no option to command-line Blat that gives you the percent ID
and the score. However, we have created scripts that include the
calculations:

-  View the perl script from the source tree:
   ```pslScore.pl`` <http://genome-source.soe.ucsc.edu/gitlist/kent.git/raw/master/src/utils/pslScore/pslScore.pl>`__
-  View the corresponding C program:
   ```pslScore.c`` <http://genome-source.soe.ucsc.edu/gitlist/kent.git/raw/master/src/utils/pslScore/pslScore.c>`__
   and associated library functions ``pslScore`` and ``pslCalcMilliBad``
   in
   ```psl.c`` <http://genome-source.soe.ucsc.edu/gitlist/kent.git/raw/master/src/lib/psl.c>`__

See our `FAQ <FAQlicense.html>`__ on source code licensing and downloads
for information on obtaining the source.

Replicating web-based Blat "I'm feeling lucky" search results
-------------------------------------------------------------

How do I generate the same search results as web-based Blat's "I'm feeling lucky" option using command-line Blat?
                                                                                                                 

The code for the "I'm feeling lucky" Blat search orders the results
based on the sort output option that you selected on the query page. It
then returns the highest-scoring alignment of the first query sequence.

If you are sorting results by "query, start" or "chrom, start",
generating the "I'm feeling lucky" result is straightforward: sort the
output file by these columns, then select the top result.

To replicate any of the sort options involving score, you first must
calculate the score for each result in your PSL output file, then sort
the results by score or other combination (*e.g.* "query, score" and
"chrom, score"). See the section on `Replicating web-based Blat percent
identity and score calculations <#blat4>`__ for information on
calculating the score.

Alternatively, you can try filtering your Blat PSL output using either
the ``pslReps`` or ``pslCDnaFilter`` program available in the Genome
Browser source code. For information on obtaining the source code, see
our `FAQ <FAQlicense.html>`__ on source code licensing and downloads.

Using BLAT for short sequences with maximum sensitivity
-------------------------------------------------------

How do I configure BLAT for short sequences with maximum sensitivity?
                                                                     

Here are some guidelines for configuring standalone Blat and
gfServer/gfClient for these conditions:

-  The formula to find the shortest query size that will guarantee a
   match (if matching tiles are not marked as overused) is: 2 \*
   *stepSize* + *tileSize* - 1
   For example, with *stepSize* set to 5 and *tileSize* set to 11,
   matches of query size 2 \* 5 + 11 - 1 = 20 bp will be found if the
   query matches the target exactly.
   The *stepSize* parameter can range from 1 to *tileSize*.
   The *tileSize* parameter can range from 6 to 15. For protein, the
   range starts lower.
   For *minMatch*\ =1 (e.g., protein), the minimum guaranteed match
   length is: 1 \* *stepSize* + *tileSize* - 1
   Note: There is also a "minimum lucky size" for hits. This is the
   smallest possible hit that BLAT can find. This minimum lucky size can
   be calculated using the formula: *stepSize* + *tileSize*. For
   example, if we use a *tileSize* of 11 and *stepSize* of 5, hits
   smaller than 16 bases won't be reported.
-  Try using *-fine*.
-  Use a large value for *repMatch* (e.g. *-repMatch* = 1000000) to
   reduce the chance of a tile being marked as over-used.
-  Do not use an *.ooc* file.
-  Do not use *-fastMap*.
-  Do not use masking command-line options.

The above changes will make BLAT more sensitive, but will also slow the
speed and increase the memory usage. It may be necessary to process one
chromosome at a time to reduce the memory requirements.

A note on filtering output: increasing the *-minScore* parameter value
beyond one-half of the query size has no further effect. Therefore, use
either the ``pslReps`` or ``pslCDnaFilter`` program available in the
Genome Browser source code to filter for the size, score, coverage, or
quality desired. For information on obtaining the source code, see our
`FAQ <FAQlicense.html>`__ on source code licensing and downloads.

Blat ALL genomes
----------------

How do I blat queries for the default genome assemblies of all organisms?
                                                                         

BLAT is designed to quickly find sequence similarity between query and
target sequences. Generally, BLAT is used to find locations of sequence
homology in a single target genome or determine the exon structure of an
mRNA. BLAT also allows users to compare the query sequence against all
of the default assemblies for organisms hosted on the UCSC Genome
Browser. The *Search ALL* feature may be useful if you have an ambiguous
query sequence and are trying to determine what organism it may belong
to.

| Selecting the "Search ALL" checkbox above the Genome drop-down list
  allows you to search the genomes of the default assemblies for all of
  our organisms. It also searches any attached hubs' Blat servers,
  meaning you can search your user-generated assembly hubs.
| The new dynamic BLAT servers allow one to perform BLAT searches on an
  unlimited number of genomes with a fixed amount of memory, however it
  takes time to swap virtual pages from the storage device. Currently
  dynamic BLAT servers are not supported for "Search ALL", and they are
  noted as skipped in the output.
| The results page displays an ordered list of all our organisms and
  their homology with your query sequence. The results are ordered so
  that the organism with the best alignment score is at the top,
  indicating which region(s) of that organism has the greatest homology
  with your query sequence. The entire alignment, including mismatches
  and gaps, must `score <../FAQ/FAQblat.html#blat4>`__ 20 or higher in
  order to appear in the Blat output. By clicking into a link in the
  *Assembly list* you will be taken to a new page displaying various
  locations and scores of sequence homology in the assembly of interest.

Blat ALL genomes: No matches found
----------------------------------

My Blat ALL results display assemblies with hits, but clicking into them reports no matches
                                                                                           

In the Blat ALL results page, the "Hits" column does not represent
alignments, instead it reports tile hits. Tile hits are 11 base kmer
matches found in the target, which do not necessarily represent
successful alignments. When one clicks the 'Assembly' link a full Blat
alignment for that genome will occur and any alignment scores
representing less than a 20 bp result will come back as no matches
found.

When you submit a sequence to the Blat ALL utility, the sequence is
compared to an index in the server. The index has been built from the
target genome, with an 11bp default stepSize. These 11-mers "tile" the
sequence as such:

::

   TGGACAACATG
              GCAAGAATCAG
                         TCTCTACAGAA

After the index is built, the first step of alignment is to read the
query (search) sequence, extract all the 11-mers, and look those up in
the genome 11-mer index currently in memory. Matches found there
represent the initial "hits" you see in the Blat ALL results page. The
next step is to look for hits that overlap or fall within a certain
distance of each other, and attempt to align the sequences between the
hit locations in target and query.

For example, if two 11-base tile hits align perfectly, it would result
in a score of 22. This is above the minimum required score of 20 (see
`Blat ALL genomes <#blat9>`__), and would be reported as an alignment.
However, there are penalties for gaps and mismatches, as well as
potential overlap (see stepsize in `BLAT
specifications <../goldenPath/help/blatSpec.html>`__), all of which
could bring the score below 20. In that case, Blat ALL would report 2
"hits", but clicking into the assembly would report no matches. This
most often occurs when there are only a few (1-3) hits reported by Blat
ALL.

Approximating web-based Blat results using gfServer/gfClient
------------------------------------------------------------

Often times using the gfServer/gfClient provides a better approximation
or even replicate of the web-based Blat results, which otherwise cannot
be found using standalone Blat. This approach mimics the Blat server
used by the Genome Browser web-based Blat. The following example will
show how to set up an hg19 gfServer, then make a query. First, download
the appropriate utility for the operating system and give it executable
permissions:

::

   #For linux
   rsync -a rsync://hgdownload.soe.ucsc.edu/genome/admin/exe/linux.x86_64/blat/ ./
   #For MacOS
   rsync -a rsync://hgdownload.soe.ucsc.edu/genome/admin/exe/macOSX.x86_64/blat/ ./

   chmod +x gfServer gfClient blat

Next, download the appropriate .2bit genome (hg19 in this example), and
run the gfServer utility with the web Blat parameters, designating the
local machine and port 1234:

::

   wget http://hgdownload.soe.ucsc.edu/goldenPath/hg19/bigZips/hg19.2bit
   ./gfServer start 127.0.0.1 1234 -stepSize=5 hg19.2bit

After a few moments, the gfServer will initialize and be ready to
recieve queries. In order to approximate web Blat, we will use the
gfClient with the following parameters, designating our input and output
files.

::

   ./gfClient -minScore=20 -minIdentity=0 127.0.0.1 1234 . input.fa out.psl

The output file ``out.psl`` should have results very similar to
web-based Blat.

Standalone or gfServer/gfClient result start positions off by one
-----------------------------------------------------------------

My standalone Blat results or gfServer/gfClient Blat results have a start position that is one less that what I see on web Blat results
                                                                                                                                       

This is due to how we store internal coordinates in the Genome Browser.
The default Blat **Output type** of **hyperlink** shows results in our
internal coordinate data structure. These internal coordinates have a
zero-based start and a one-based end. See the following `FAQ
entry </FAQ/FAQtracks#tracks1>`__ for more information.

If the **Output type** is changed to **psl** on web Blat, the same
zero-based half open coordinate results will be seen as the standalone
Blat and gfServer/gfClient procedures.

Protein-translated BLAT having different results
------------------------------------------------

Protein-translated BLAT (protein or translated RNA queries) uses the
standard vertebrate genetic code. It will be slightly less sensitive on
mitochondria and species using other genetic codes. More information on
standard genetic codes can be found on the `NCBI
website <https://www.ncbi.nlm.nih.gov/Taxonomy/taxonomyhome.html/index.cgi?chapter=cgencodes>`__.
Additional details on mitochondria codon tables can be found on the
`Wikiwand
website <https://www.wikiwand.com/en/DNA_and_RNA_codon_tables>`__.
