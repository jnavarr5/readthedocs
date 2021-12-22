Genome Browser Tracks
=====================

Topics
------

-  `List of tracks available for a specific assembly <#tracks0>`__
-  `Database/browser start coordinates differ by 1 base <#tracks1>`__
-  `mRNA-associated results <#tracks2>`__
-  `Correspondence of Genome Browser mRNA positions to those of OMIM
   genes <#tracks3>`__
-  `Position changes of features <#tracks4>`__
-  `Evaluating possible alternative splices <#tracks6>`__
-  `Matching exons and protein sequence <#tracks7>`__
-  `Cause of duplicated gene <#tracks9>`__
-  `Protein doesn't begin with methionine <#tracks11>`__
-  `Doing an orthology track analysis of a protein <#tracks12>`__
-  `Quality benchmarks for predicted genes <#tracks14>`__
-  `Display conventions for gene prediction tracks <#tracks15>`__
-  `Viewing detailed displays in conservation tracks <#tracks16>`__
-  `Negative strand coordinates in PSL files <#tracks17>`__
-  `Inconsistency in stop codon treatment in GTF tracks <#tracks18>`__
-  `Obtaining clones referenced in Genome Browser <#tracks19>`__
-  `Locating centromeres and telomeres <#tracks20>`__
-  `Determining the table name for an annotation track <#tracks21>`__
-  `Unexpected results in UCSC RefSeq track <#tracks22>`__

--------------

`Return to FAQ Table of Contents <index.html>`__

List of tracks available for a specific assembly
------------------------------------------------

How can I find out which tracks have been released for the assembly in which I'm interested?
                                                                                            

The `Release Log </goldenPath/releaseLog.html>`__ contains lists of the
published tracks and release dates for the current set of genome
assemblies available on our site. It also shows version information for
the assemblies of other species used in comparative genomics tracks.

Database/browser start coordinates differ by 1 base
---------------------------------------------------

I am confused about the start coordinates for items in the refGene table. It looks like you need to add "1" to the starting point in order to get the same start coordinate as is shown by the Genome Browser. Why is this the case?
                                                                                                                                                                                                                                    

Our internal database representations of coordinates always have a
zero-based start and a one-based end. We add 1 to the start before
displaying coordinates in the Genome Browser. Therefore, they appear as
one-based start, one-based end in the graphical display. The refGene.txt
file is a database file, and consequently is based on the internal
representation.

We use this particular internal representation because it simplifies
coordinate arithmetic, i.e. it eliminates the need to add or subtract 1
at every step. If you use a database dump file but would prefer to see
the one-based start coordinates, you will always need to add 1 to each
start coordinate.

If you submit data to the browser in position format (chr#:##-##), the
browser assumes this information is 1-based. If you submit data in any
other format (BED (chr# ## ##) or otherwise), the browser will assume it
is 0-based. You can see this both in our liftOver utility and in our
search bar, by entering the same numbers in position or BED format and
observing the results. Similarly, any data returned by the browser in
position format is 1-based, while data returned in BED format is
0-based.

For a detailed explanation, please see our blog entry for the `UCSC
Genome Browser coordinate counting
systems <http://genome.ucsc.edu/blog/the-ucsc-genome-browser-coordinate-counting-systems/>`__.

mRNA-associated results
-----------------------

Sometimes when I type in the name of a gene -- e.g. DAO (D aminoacid oxidase) -- the Genome Browser returns a list that includes the gene entry on the assembly, but also contains links to several other genes and aligned mRNAs. What is the relationship between my gene of interest and these results?
                                                                                                                                                                                                                                                                                                          

The gene search results are obtained from scanning the RefSeq and Known
Genes tracks, which are typically based on non-redundant relatively high
quality mRNAs. A small fraction of RefSeqs are based on DNA level
annotations. In most cases, there is a HUGO Gene Nomenclature Committee
symbol or other biological name associated with the gene. In the case of
the RefSeq track, the association between these names and the accession
is maintained at NCBI and is also present in the refLink table.

The mRNA search results are obtained by scanning data associated with
the GenBank record for mRNAs. These are often redundant, but
occasionally contain something useful that has not yet made it into
RefSeq. The mRNA information is often useful because the people who
deposited the mRNA into GenBank are listed in the record. Frequently
these same people have written interesting articles on the gene or may
serve as a source of information on the gene.

Correspondence of Genome Browser mRNA positions to those of OMIM genes
----------------------------------------------------------------------

If I do a Genome Browser search for an mRNA sequence using its GenBank accession number, will I always get the same cytogenetic location as that given by OMIM for the gene?
                                                                                                                                                                            

Not always. Sometimes the Genome Browser will return more than one
location when there are recent duplication or assembly problems in the
human genome. In these cases, usually one of the locations will agree
with OMIM. In a few rare instances involving not-quite-so-recent
duplications in the genome, UCSC will attempt to assign it uniquely, but
OMIM will think it belongs someplace just under our threshold. A Blat
search of the cDNA is very informative in these cases. In rare cases,
UCSC or NCBI may have made a data processing error. For the vast
majority of cases, however, the two sites do match.

Position changes of features
----------------------------

Yesterday I was looking at a contig in a specific location, and today the location has changed. What happened?
                                                                                                              

Check that you are using the same assembly version that you were using
yesterday. Features may change positions within a genome between
releases, particularly if they are located in an area of the genome that
is still in draft form. See `Coordinate changes between
assemblies <FAQreleases.html#release7>`__ for more information.

Evaluating possible alternative splices
---------------------------------------

When you view results from the Genome Browser, how do you determine whether the alternative splice is real or if it is a sequencing artifact?
                                                                                                                                             

It's a very good idea to click into the alignment and check that it
looks clean at a detailed level and that the splice sites are
reasonable. If you have an alternate exon, it is also good to Blat just
that exon. Occasionally you may encounter a recent tandem duplication
event that encompasses a single exon, which can masquerade as
alternative splicing on the graphical display. If it's an EST, check to
see if it is from a RAGE library. If so, alternative promoters are
likely to be an artifact of the RAGE process rather than biological. If
the alternative splice still looks good after these checks, the next
step is to do some RT-PCR in the lab.

Matching exons and protein sequence
-----------------------------------

I am working with alternatively spliced forms of an enzyme. How can I use the database to identify exons and exactly match them to protein databases (i.e. identify the exons based on a protein sequence and vice versa)?
                                                                                                                                                                                                                          

If you have a protein sequence, you can use `Blat <../cgi-bin/hgBlat>`__
to align your sequence to the desired genome. In the ACTIONS column on
the Blat search results page, click the details link to view details of
exons blocks. Alternatively, click the browser link to display the
search results in the Genome Browser. Look for instances in which a gene
from the Blat query track aligns exactly or very similarly to an entry
in the Known Genes track. Click on the entry to display details about
the gene. The SWISS-PROT link on the details page will lead you to more
details about this protein.

Follow a similar procedure with an mRNA sequence. If there is no
corresponding entry in the Known Genes or RefSeq track, then
congratulations, you may have found an unreported new gene. You may want
to doublecheck the results using NCBI BLAST.

Cause of duplicated gene
------------------------

I have found a gene that has two identical copies on different chromosomes within the Genome Browser. Is this possible?
                                                                                                                       

One of the copies may be an artifactual duplication resulting from
unavoidable compromises in the assembly process. However, there do exist
very recent authentic duplication events. Frequently these are
pericentromeric or subtelomeric.

There are several checks you can make to determine whether you are
viewing an actual duplication or an assembly process artifact. Create a
Blat track from the gene's mRNA and examine the details page for a match
that is too perfect. Then, open the Genome Browser with the duplication
and gap tracks set to dense mode. Look for problems in the flanking
sequence in the duplication track. Also look for suspicious placement of
the gene, for example inside the intron of another gene. You may also
want to follow the OMIM link to look for hand-curated experimental
literature summaries. BLASTing the mRNA against a more recent assembly
may provide another line of evidence.

Protein doesn't begin with methionine
-------------------------------------

I am looking at a human protein that the Genome Browser associates with a particular gene. According to the Genome Browser, its amino acid sequence doesn't start with M (methionine). I thought nuclear-encoded human proteins always began with methionine?
                                                                                                                                                                                                                                                             

The UCSC genome browser uses translated mRNA data exactly as supplied to
GenBank by the original sequencing authors. Any errors at GenBank
propagate through many other databases and tools. To work effectively in
a bioinformatic area subject to errors, it is a good idea to seek
supporting data for any unusual finding.

To further investigate this example, you may want to use Blat or BLAST
to recover other close members of this gene family. By using comparative
alignment, you may discover that the 5' UTR in the mRNA for this protein
was likely misinterpreted as coding sequence and that the protein begins
with methionine as expected. The error may also be caused by an
underlying mRNA in GenBank that stops short of the initiator methionine.
In this case, you could use ESTs, other mRNAs, and Blat or BLAST of
paralogs against unfinished genome sequence to extend the mRNA to a more
plausible full-length sequence.

Doing an orthology track analysis of a protein
----------------------------------------------

I am working on a lipase called hormone-sensitive lipase (HSL) gene ID NM_010719. I am trying to see if there is any protein that has the same domain organization as HSL. Will doing an orthology track of the protein help me to get an answer? How do I do the orthology track analysis?
                                                                                                                                                                                                                                                                                           

You can accomplish this by using Blat and the Genome Browser Superfamily
track. Blat the protein sequence from the NCBI RefSeq record, then
choose the choose the Browser display option to view your search results
in the Genome Browser window. Set the RefSeq and Superfamily tracks to
full display mode. The RefSeq track will contain the entry LIPE, and you
will find the corresponding entry ENSP00000244289 in the Superfamily
track. Click the Superfamily entry, and then click the Superfamily link
on the details page that displays. This will open a browser for the
Superfamily site. Click "alpha/beta-Hydrolases" to open the Structural
Classification of Proteins (SCOP) page. There you will find multiple
families listed under this Superfamily, including the lipase in which
you're interested.

Quality benchmarks for predicted genes
--------------------------------------

Do you offer any benchmarks of quality and quantity of known and predicted genes shown in the Acembly, Ensembl, Genscan, Fgenesh++, Twinscan, and TIGR Gene Index gene prediction tracks?
                                                                                                                                                                                         

These tracks are contributed by institutional programs outside of UCSC.
You can access links to their home pages and relevant publications from
the description pages associated with the tracks (which can be viewed by
clicking on the grey mini-button to the left of the track). You may also
obtain supplemental information from the `Users
Guide <../goldenPath/help/hgTracksHelp.html>`__ and the `Credits
page <../goldenPath/credits.html>`__. Methods and quality checks are
often described in greater detail there. No uniform benchmarking system
exists. Finished chromosomes are commonly used, but even here the
experimental work continues today on delineating genes.

UCSC does not provide summary statistics for these tracks. However,
these may be easily compiled from the appropriate tables in the `Table
Browser <../cgi-bin/hgTables>`__. The number of predicted genes and
exons are easily compared. Some quality checks can also easily be run,
such as how many of the predicted gene models are incomplete (e.g. the
transcription start coordinate is the same as the CDS start).

Looking at almost any coordinate position within the Genome Browser, you
can see that there are discrepancies between the predicted gene tracks,
as well as further inconsistencies with respect to experimental data
tracks such as spliced ESTs. The RefSeq track also contains genes of
uncertain status, e.g. lack of initiator methionine. Thus, it is not
clear where one can obtain a gold standard for measuring gene prediction
quality. A reference set might be hand-curated out of recent journal
articles of exceptional thoroughness. UCSC does not currently maintain
such a resource.

Display conventions for gene prediction tracks
----------------------------------------------

What is the significance of the thinner blocks displayed at the beginning and end of a gene in the browser?
                                                                                                           

The varying thickness of features in the Genome Browser gene tracks
denotes the various structural features of a gene, such as exons,
introns, and untranslated regions (UTRs). The thickest parts of the
track indicate the coding exon regions within the gene. The slightly
thinner portions at the leading and trailing ends of the gene track show
the 5' and 3' UTRs. Introns are depicted as lines with arrows indicating
the direction of transcription.

Some aspects of the graphical representation are inevitably lost upon
rescaling. For example, coding exons are given preference at coarse
scales. For single exon genes, there is no place to put the strand
orientation wedges, and therefore the feature's detail page must be
consulted.

For more information about annotation track display conventions within
the Genome Browser, consult the `User's
Guide <../goldenPath/help/hgTracksHelp.html>`__.

Viewing detailed displays in conservation tracks
------------------------------------------------

When I click on a region in the Human/Mouse Evolutionary Conservation Score track, it doesn't give me detailed information.
                                                                                                                           

The track is defaulting to dense display mode because the size of the
track's displayed region is too large. Unfortunately, this particular
track doesn't have good visual cues to show you when it's defaulting to
dense mode. If you zoom in on the region in which you're having the
problem, you should be able to display the details page.

Negative strand coordinates in PSL files
----------------------------------------

I've noticed that the blatFugu table has two characters representing the strand. Also, I've noticed that the starting/ending positions of the blocks don't fall within the start/end positions of the chromosome target.
                                                                                                                                                                                                                        

When the second character in the strand is "-", the coordinates of the
comma-separated list of tStarts are reverse-complemented relative to
tStart, much as qStarts behave when the first letter in the strand is
"-".

Inconsistency in stop codon treatment in GTF tracks
---------------------------------------------------

I've been doing some comparative gene set analysis using the gene annotation tracks and I believe I have run into an inconsistency in the way that stop codons are treated in the annotations. Looking at the Human June 2002 assembly, the annotations for Ensembl, Twinscan, SGP, and Geneid appear to exclude the stop codon in the coding region coordinates. All of the other gene annotation sets include the stop codon as part of the coding region. My guess is that this inconsistency is the result of the gene sets being imported from different file formats. The `GTF2 format <http://mblab.wustl.edu/GTF2.html>`__ does not include the stop codon in the terminal exon, while the GenBank format does, and the GFF format does not specify what to do.
                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       

Your guess is correct. We haven't gotten around to fixing this
situation. A while ago, the Twinscan group made a GTF validator. It
interpreted the stop codon as *not* part of the coding region. Prior to
that, all GFF and GTF annotations that we received did include the stop
codon as part of the coding region; therefore, we didn't have special
code in our database to enforce it. In response to the validator,
Ensembl, SGP and Geneid switched their handling of stop codons to the
way that Twinscan does it, hence the discrepancy.

Obtaining clones referenced in Genome Browser
---------------------------------------------

Is it possible to purchase the chromosome clones referenced in the Genome Browser?
                                                                                  

You can find further information about a specific clone by clicking on
the clone name link on the details page for the item. This links to the
NCBI Clone Registry website, which lists extensive details about the
clone, including distributor information.

Locating centromeres and telomeres
----------------------------------

How do I find the positions of the centromeres and telomeres in a particular assembly?
                                                                                      

This information can be found in the "gap" database table. Use the Table
Browser to extract it. To do this, select your assembly and the gap
table, then click the " filter Create" button. Set the "type" field to
``centromere telomere`` (separated by a space). For help using the Table
Browser, visit the `User's
Guide <../goldenPath/help/hgTablesHelp.html>`__.

Determining the table name for an annotation track
--------------------------------------------------

How do I find the name of the database table that contains the data for a particular annotation track?
                                                                                                      

Each annotation track in the Genome Browser has one or more database
tables associated with it. To find the name of the primary table,
navigate to the schema page. You will find the schema page by pressing
the "mini-button" to the left of the annotation track display, or
clicking the hyper-linked track name in the track controls (below the
display). From the resulting description page, follow the "View table
schema" link. Finally, on the schema page, you will find the name of the
database table near the top of the page listed after the "Primary Table"
label.

Unexpected results in UCSC RefSeq track
---------------------------------------

Why do some annotations differ in the UCSC RefSeq track compared to NCBI's Reference Sequence Database?
                                                                                                       

Historically, NCBI RefSeq coordinates were not directly available for
building tracks in the UCSC Genome Brower. Instead of using coordinates
to map annotations, mappings to the reference assembly were conducted
using `BLAT <../FAQ/FAQblat.html>`__ (BLAST-like alignment tool)
alignment methods. This BLAT alignment method has caused some
discrepancies from the NCBI RefSeq database. Most discrepancies arise
when the BLAT-generated annotations align to multiple regions where the
sequence in the assembly is either identical or nearly identical. In
essence, by using BLAT to align the sequence, a single transcript could
result in matching to multiple novel places across the genome, or
alignments of small exons could differ slightly in final coordinates
within the region of a gene rich with repeats. BLAT-generated RefSeq
track methods are described in corresponding track description pages
(e.g., `RefSeq track description for
hg19) <../cgi-bin/hgTrackUi?db=hg19&g=refGene>`__.

In 2017, NCBI RefSeq coordinates for hg38 were used for generating
non-discrepant RefSeq tracks in the UCSC Genome Browser. This new `NCBI
RefSeq track <../cgi-bin/hgTrackUi?db=hg38&g=refSeqComposite>`__ in the
UCSC Genome Browser displays identical RNA coordinates to annotations in
the `NCBI Reference Sequence
Database <https://www.ncbi.nlm.nih.gov/refseq/>`__. Please note that
when annotations do map to multiple loci, the NCBI RefSeq track displays
unique identifiers for each locus, while the UCSC RefSeq track retains
the same identifier.

For more information and future plans to integrate coordinate-generated
NCBI RefSeq tracks for other assemblies, please see the `NCBI RefSeq
track blog
post <http://genome.ucsc.edu/blog/the-new-ncbi-refseq-tracks-and-you/>`__.
