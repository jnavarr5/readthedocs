Genes and Gene tracks
=======================================

-  `What is a gene? <#gene>`__
-  `What is a transcript and how is it related to a
   gene? <#genestrans>`__
-  `What is a gene name? <#genename>`__
-  `What are the most common gene transcript tracks? <#mostCommon>`__
-  `I think this transcript looks strange, what shall I do? <#wrong>`__
-  `What are Ensembl and GENCODE and is there a difference? <#ens>`__
-  `What are the differences among GENCODE, Ensembl and
   RefSeq? <#ensRefseq>`__
-  `For the human assembly hg19/GRCh37: What is the difference between
   "UCSC Genes" track, the "GENCODE" track and the "Ensembl Genes"
   track? <#hg19>`__
-  `For the human assembly hg38/GRCh38: What are the differences between
   the "GENCODE" and "All GENCODE" tracks? <#hg38>`__
-  `What is the difference between GENCODE comprehensive and
   basic? <#gencode>`__
-  `What is the difference between "NCBI RefSeq" and "UCSC
   RefSeq"? <#ncbiRefseq>`__
-  `What is the best gene track for mitochondrial gene
   annotations? <#mito>`__
-  `How shall I report a gene transcript in a manuscript? <#report>`__
-  `What is CCDS? <#ccds>`__
-  `How can I show a single transcript per gene? <#justsingle>`__
-  `How can I download a file with a single transcript per
   gene? <#singledownload>`__
-  `This is rather complicated. Can you tell me which gene transcript
   track I should use? <#whatdo>`__
-  `Does UCSC provide GTF/GFF files for gene models? <#gtfDownload>`__

--------------

`Return to FAQ Table of Contents <index.html>`__

The basics
----------

The genome browser contains many gene annotation tracks. Our users often
wonder what these contain and where the information that we present
comes from.

What is a gene?
               

The exact definition of "gene" depends on the context. In the context of
genome annotation, a gene has at least a name and is defined by a
collection of related RNA transcript sequences ("isoforms"). The naming
of genes and the assignment of the most important transcript sequences
is often done manually by a group of biological literature curators. For
human, genes names are created by the `Human Gene Nomenclature Committee
(HGNC, formerly HUGO) <https://www.genenames.org/>`__. Non-human species
have similar annotation groups, e.g. Mouse Genome Informatics, Wormbase,
Flybase, etc.

What is a transcript and how is it related to a gene?
                                                     

In the Genome Browser, transcript tracks often end with the word
"Genes", e.g. "Ensembl Genes", "NCBI RefSeq Genes", or "UCSC Genes".
Despite the name, items in these tracks actually represent transcripts
on chromosomes of a genome assembly

Transcripts are defined as RNA molecules that are made from a DNA
template. Databases like the ones at the National Library of Medicine's
NCBI or the European Bioinformatics Institute (EBI) collect these
transcript sequences from biologists working on a gene. Every transcript
has a unique identifier (accession), a gene that it is assigned to, a
sequence, and a list of exon chrom/start/end coordinates on a
chromosome.

Most genes have multiple transcripts associated with them. Some of these
transcripts differ only in the "untranslated regions" (UTRs), while the
coding sequence and resulting protein stay the same. Some transcripts
may instead stop in the middle of a coding exon, which changes the
protein. Some transcripts may even put the exons together in a different
way or skip some exons entirely.

While most genes are associated with multiple transcripts, each
transcript is only assigned to a single gene (at least in databases). In
other words, different genes never share the same transcript. For
example, using the databases by NCBI, the gene with the gene symbol
`BRCA1 <https://www.ncbi.nlm.nih.gov/gene/672#>`__ has 5 protein-coding
transcripts or isoforms. The first transcript has the NCBI accession
number
`NM_007294.3 <https://www.ncbi.nlm.nih.gov/nuccore/NM_007294.3>`__ which
produces the protein with the accession
`NP_009225.1 <https://www.ncbi.nlm.nih.gov/protein/NP_009225.1>`__. In
the human genome, it is located on chromosome 17, where it is comprised
of `23 exons <https://www.ncbi.nlm.nih.gov/nuccore/U14680>`__. On the
version hg38/GRCh38 of the human genome, these exons cover the DNA
nucleotides 43044295 to 43125483.

What is a gene or transcript accession?
                                       

Gene symbols such as BRCA1 are easy to remember but sometimes change and
are not specific to an organism. Therefore most databases internally use
unique identifiers to refer to sequences and some journals require
authors to use these in manuscripts.

The most common accession numbers encountered by users are either from
Ensembl, GENCODE or RefSeq. Human Ensembl/GENCODE gene accession numbers
start with ENSG followed by a number and version number separated by a
dot, e.g. "ENSG00000012048.21" for latest BRCA1. Every ENSG-gene has at
least one transcript assigned to it. The transcript identifiers start
with with ENST and are likewise followed by a version number, e.g.
"ENST00000619216.1". Additional details on Ensembl IDs can be found on
the `Ensembl FAQ page <https://uswest.ensembl.org/Help/Faq?id=488>`__.

NCBI refers to genes with plain numbers, e.g. 672 for BRCA1. Manually
curated RefSeq transcript identifiers start with NM\_ (coding) or NR\_
(non-coding), followed by a number and version number separated by a
dot, e.g. "NR_046018.2". If the transcript was predicted by the NCBI
Gnomon software, the prefix is XM\_ but these are rare in human. A table
of these and other RefSeq prefixes can be found on the `NCBI
website <https://www.ncbi.nlm.nih.gov/books/NBK21091/table/ch18.T.refseq_accession_numbers_and_mole/?report=objectonly>`__.

What are the most common gene transcript tracks?
                                                

Researchers sequence `cDNA
sequences <https://en.wikipedia.org/wiki/Complementary_DNA>`__ and send
these to NCBI Genbank. The Genome Browser shows these sequences in the
Genbank or the `EST track <../cgi-bin/hgTrackUi?db=hg38&g=est>`__ (if
the cDNA is just a single read from the 5' or 3' end). From the
alignment of the cDNAs and ESTs, the NCBI RefSeq group manually creates
a smaller set of representative transcripts which we display as the
`RefSeq Curated <../cgi-bin/hgTrackUi?db=hg38&g=refSeqComposite>`__
track. Automated programs like UCSC's or Ensembl's gene build software
do the same, just in software, which is more systematic but also more
error-prone. With the arrival of GENCODE, Ensembl added a manual
curation to their human and mouse transcripts. NCBI has added an
automated prediction software (Gnomon) which we show in the "`RefSeq
Predicted <../cgi-bin/hgTrackUi?db=hg38&g=refSeqComposite>`__" track.

There are many other tracks in the group "Genes and Gene Predictions".
`Genscan <../cgi-bin/hgTrackUi?db=hg38&g=genscan>`__ and
`N-Scan <../cgi-bin/hgTrackUi?db=hg19&g=nscanGene>`__ are older
transcript predictor algorithms that are based on the genome sequence
alone. `Augustus <../cgi-bin/hgTrackUi?db=hg38&g=augustusGene>`__ and
`AceView <../cgi-bin/hgTrackUi?db=hg19&g=acembly>`__ are automated
gene-predictors that use cDNA and EST data. These and similar gene
tracks are only relevant when you are working on a particular locus
where you think that the manually curated gene models (Ensembl and
RefSeq) have errors.

To illustrate differences between the most common gene tracks, here is
an overview of a few different tracks on human (hg38) and how many
transcripts they contain as of March 2019:

====================================== =========================
**Track name**                         **Number of transcripts**
====================================== =========================
Known Gene (Gencode comprehensive V29) 226,811
Known Gene (Gencode basic V29)         112,634
NCBI RefSeq Predicted Transcripts      94,389
UCSC RefSeq (Curated)                  80,694
NCBI RefSeq Curated                    73,080
CCDS                                   32,506
====================================== =========================

I think this transcript looks strange, what shall I do?
                                                       

The Genome Browser Group only displays transcripts provided by others.
But both RefSeq and Gencode have dedicated staff that look manually at
each and every transcript and they know everything there is to know
about gene models. They are happy to answer your questions and they can
change the transcript annotation. Submit your questions via the `RefSeq
contact
form <https://www.ncbi.nlm.nih.gov/projects/RefSeq/update.cgi>`__ or the
`Gencode context
form. <https://www.gencodegenes.org/pages/contact.html>`__

The differences
---------------

Some of our gene tracks look similar and contain very similar
information which can be confusing.

What are Ensembl and GENCODE and is there a difference?
                                                       

Officially, the Ensembl and GENCODE gene models are the same. On the
latest human and mouse genome assemblies (hg38 and mm10), the
identifiers, transcript sequences, and exon coordinates are almost
identical between equivalent Ensembl and GENCODE versions (excluding
`alternative sequences <FAQdownloads.html#downloadAlt>`__ or `fix
sequences <FAQdownloads.html#downloadFix>`__).

GENCODE uses the UCSC convention of prefixing chromosome names with
"chr", e.g. "chr1" and "chrM", but Ensembl calls these "1" or "MT". At
the time of writing (Ensembl 89), a few transcripts differ due to
conversion issues. In addition, around 160 PAR genes are duplicated in
GENCODE but only once in Ensembl. The differences affect fewer than 1%
of the transcripts. Apart from gene annotation itself, the links to
external databases differ.

The `GENCODE Release
History <https://www.gencodegenes.org/human/releases.html>`__ shows the
release dates and can be linked to corresponding Ensembl releases. You
can download the gene transcript models from the website
https://gencodegenes.org or from http://ensembl.org. For most
applications, the files distributed on the GENCODE website should be
easier to use, as the third party database links are easier to parse and
the sequence identifiers match the UCSC genome files, at least for the
primary chromosomes.

Additional information on this question can be found on the `GENCODE FAQ
page <https://www.gencodegenes.org/pages/faq.html>`__.

What are the differences among Ensembl, GENCODE and RefSeq?
                                                           

Different institutions have different rules on how they annotate genes.
E.g. RefSeq's criteria are more stringent, so there are fewer RefSeq
transcripts than Ensembl/GENCODE transcripts. Also, RefSeq transcripts
have their own sequences independent of the genome assembly, so certain
population-specific variants may be in RefSeq that are entirely missing
from the reference genome sequence. This has the important implication
that the position of genome variants are harder to map to RefSeq
transcripts than for GENCODE since RefSeq transcripts can have
additional sequence or missing sequence relative to the genome.

The links from either transcript model to other gene-related databases
are different. In general, it seems that high-throughput sequencing data
results, e.g. RNA-seq, are often using Ensembl/GENCODE annotations and
human genetics results are reported using RefSeq annotations. It depends
on your particular project which gene model set you want to use. Over
time, the two transcript databases have been and are becoming more
similar.

For the human assembly hg19/GRCh37 and mouse mm9/NCBI37: What is the difference between UCSC Genes, the "GENCODE Gene Annotation" track and the "Ensembl Genes" track?
                                                                                                                                                                      

The "`UCSC Genes <../cgi-bin/hgTrackUi?db=hg19&g=knownGene>`__" track,
also called "Known Genes", is available only on assemblies before hg38.
It was built with a gene predictor developed at UCSC. This gene
predictor uses protein, EST and cDNA annotations to derive a relatively
restricted gene transcript set. The software is no longer in use and
there are no plans to release the track on newer human assemblies. It
was last used for the mm10 mouse assembly.

The "`GENCODE Gene
Annotation <../cgi-bin/hgTrackUi?db=hg19&g=wgEncodeGencodeSuper>`__"
track contains data from all versions of GENCODE. "`Ensembl
Genes <../cgi-bin/hgTrackUi?db=hg19&g=ensGene>`__" track contains just a
single Ensembl version. See the previous question for the differences
between Ensembl and GENCODE.

For the human assembly hg38/GRCh38 and mouse mm10/GRCm38: What are the differences between the "GENCODE" and "All GENCODE" tracks?
                                                                                                                                  

"`GENCODE <../cgi-bin/hgTrackUi?db=hg38&g=knownGene>`__" is the default
gene track on hg38 (similar to "Known Genes" on hg19), which means that
it is associated with a large amount of third party information when you
click on a gene. This related information is also available using the
Table Browser. This GENCODE track is updated periodically to match the
latest GENCODE release. "`All
GENCODE <../cgi-bin/hgTrackUi?db=hg38&g=wgEncodeGencodeSuper>`__" is a
super-track that contains all versions of GENCODE as sub-tracks, but
these tracks have less third-party information. Sub-tracks are never
removed from "All GENCODE", and new sub-tracks are added as there are
additional GENCODE releases.

What is the difference between "GENCODE Comprehensive" and "GENCODE Basic"?
                                                                           

The "`GENCODE <../cgi-bin/hgTrackUi?db=hg38&g=knownGene>`__" track
offers a "basic" gene set, and a "comprehensive" gene set. The "basic"
gene set represents a subset of transcripts that GENCODE believes will
be useful to the majority of users. The "basic" gene set is defined as
follows in the `GENCODE
FAQ <https://www.gencodegenes.org/pages/tags.html>`__:

*"Identifies a subset of representative transcripts for each gene;
prioritises full-length protein coding transcripts over partial or
non-protein coding transcripts within the same gene, and intends to
highlight those transcripts that will be useful to the majority of
users."*

A more comprehensive definition can also be found in the `Ensembl
FAQ <https://uswest.ensembl.org/info/genome/genebuild/transcript_quality_tags.html#basic>`__.
By default, the track displays only the "basic" set. In order to display
the complete "comprehensive" set, the box can be ticked at the top of
the `GENCODE track description
page <../cgi-bin/hgTrackUi?db=hg38&g=knownGene>`__.

|Turning on comprehensive gene set|

What is the difference between "NCBI RefSeq" and "UCSC RefSeq"?
                                                               

RefSeq gene transcripts, unlike GENCODE/Ensembl/UCSC Genes, are
sequences that can differ from the genome. They need to be aligned to
the genome to create annotations and UCSC and NCBI create alignments
with different software (BLAT and splign, respectively). The advantages
of the UCSC alignments are that they are updated constantly even for
older assemblies, such as GRCh37/hg19. The advantage of NCBI alignments
are that they are placed manually to a chromosome location and are the
official alignments, e.g. for databases and manuscripts. Therefore, we
recommend working with the NCBI annotations and when an assembly has an
"NCBI RefSeq" track, we show it by default and hide the "UCSC RefSeq"
track. The only exception may be hg19 (see the note at the end of this
section).

The UCSC alignments can differ from the NCBI alignments for two reasons:

**Very similar transcripts:** Let's take the case of two
almost-identical transcripts sequences in RefSeq, with two genes in the
genome where they could be placed. NCBI has a rule to place every
transcript only once, and transcripts are manually tied to a chromosome
band or location by NCBI, so each gene will get one and only one
transcript of two. NCBI RefSeq will have two genes with one transcript
each. UCSC RefSeq though places all transcripts where they align at very
high identity, so both genes will get annotated with both transcripts.
For example, the transcript NM_001012276 has three almost-identical
possible placements to the genome in the UCSC RefSeq track, as it is
entirely alignment-based without any manual filtering, but
NM_001012276.3 is shown at a single location in the NCBI RefSeq track,
as the NCBI software will only retain the alignment at the manually
annotated location. It may be good to know about almost-identical
alignments when doing genomic analysis or manual inspection of NGS read
alignments, but for clinical reporting purposes or other automated
analyses, we strongly recommend to use the NCBI RefSeq track.

**Unclear exon boundaries:** In some rare cases, the NCBI and UCSC exon
boundaries differ. This happens especially when sequence deletions in
the genome make the placement very difficult. Activating both RefSeq and
UCSC RefSeq tracks helps you investigate the differences. Activating the
RefSeq Alignments track shows NCBI's splign alignments in more detail,
including double lines where both transcript and genomic sequence are
skipped in the alignment. When available, the RefSeq Diffs subtrack may
be helpful too. The upcoming `MANE gene
set <https://ncbiinsights.ncbi.nlm.nih.gov/2018/10/11/matched-annotation-by-ncbi-and-embl-ebi-mane-a-new-joint-venture-to-define-a-set-of-representative-transcripts-for-human-protein-coding-genes/>`__
will contain a set of high-quality transcripts that are 100% alignable
to the genome and are part of both RefSeq and Ensembl/GENCODE but at the
time of writing this project is at an early stage.

An anecdotal and rare example is SHANK2 and SHANK3 in hg19. It is
impossible for either NCBI or BLAT to get the correct alignment and gene
model because the genome sequence is missing for part of the gene. NCBI
and BLAT find slightly different exon boundaries at the edge of the
problematic region. NCBI's aligner tries very hard to find exons that
align to any transcript sequence, so it calls a few small dubious
"exons" in the affected genomic region. GENCODE V19 also used an aligner
that tried very hard to find exons, but it found small dubious "exons"
in different places than NCBI. The `RefSeq
Alignments <../cgi-bin/hgTrackUi?db=hg38&g=refSeqComposite>`__ subtrack
makes the problematic region very clear with double lines indicating
unalignable transcript sequence.

**Data format:**

A small difference is the data format, which matters if you integrate
our files into pipelines: The refGene table qName field stores the
RefSeq accession but without the version number. The ncbiRefSeq tables
show the full accession, with the version number. To add the version
number to the refGene table, use a MySQL command like this:

::

   SELECT matches,misMatches,repMatches,nCount,qNumInsert,qBaseInsert,tNumInsert,tBaseInsert,strand,concat(qName, '.', gbSeq.version),qSize,qStart,qEnd,tName,tSize,tStart,tEnd,blockCount,blockSizes,qStarts,tStarts from refSeqAli, hgFixed.gbSeq WHERE refSeqAli.qname=gbSeq.acc

. To remove the transcripts on haplotypes, add this condition at the
end:

::

   and tName NOT LIKE '%_hap%' AND tName not like '%_alt%' AND tNAME NOT LIKE '%_fix%'

.

A word of caution on the NCBI RefSeq track on hg19: NCBI is not fully
supporting hg19 anymore. As a result, some genes are not located on the
main chromosomes in anymore. An example is NM_001129826/CSAG3. For hg19,
you may prefer UCSC RefSeq for now.

What is the best gene track for mitochondrial gene annotations
--------------------------------------------------------------

The mitochondrial sequence included in assembly sequence files is very
special and most of what has been explained on this page does not apply
to the mitochondrial gene annotations. For most assemblies in the Genome
Browser, the sequence name of the mitochondrial genome is "chrM".

For hg19, no mitochondrial genome was originally published. The UCSC
Genome Browser added a chrM sequence that was not the mitochondrial
genome sequence later selected by NCBI for GRCh37. This is why **the
current hg19 version contains two mitochondrial sequences, the old one
called "chrM" and the current GRCh37 reference, called "chrMT"**. The
issue is described in detail in our `hg19 sequence download
instructions <https://hgdownload.soe.ucsc.edu/goldenPath/hg19/bigZips/README.txt>`__.
If you use hg19 today, chrMT should be considered the current
mitochondrial sequence, chrM is only supported for backwards
compatibility and legacy annotation files.

For chrM or chrMT (on hg19), the GENCODE tracks contain the same gene
annotations, but RefSeq annotations only exist on chrM. Both databases
import their mitochondrial gene annotation directly from the rCRS RefSeq
record `NC_012920.1 <https://www.ncbi.nlm.nih.gov/nuccore/251831106>`__.
The annotation was provided by
`Mitomap.org <https://www.mitomap.org/MITOMAP>`__, which provides
detailed documentation about the `the history of this
sequence <https://www.mitomap.org/foswiki/bin/view/MITOMAP/MitoSeqs>`__.

How shall I report a gene transcript in a manuscript?
-----------------------------------------------------

When reporting on GENCODE/Ensembl transcripts, please specify the ENST
identifier. It is often helpful to also specify the Ensembl release,
which is shown on the details page, when you click onto a transcript.

When reporting RefSeq transcripts, e.g. in HGVS, prefer the "NCBI
RefSeq" track over the "UCSC RefSeq track". Please specify the RefSeq
transcript ID and also the RefSeq annotation release.

-  The RefSeq transcript ID is the sequence of the transcript, the
   NM_xxxxx.y accession. The version is separated with a dot. Different
   RefSeq transcript versions have different sequences (for example,
   more sequence may be added to the UTRs or even the CDS), and so the
   transcript coordinates can change from one version to the next, which
   is why reporting the version of the transcript is helpful for
   readers, e.g. report NM_012309.4, not NM_012309.
-  The RefSeq annotation release captures the mapping of all transcript
   sequences to the genome. It is shown on our transcript details page,
   when you click a transcript. It looks like "Annotation Release 105
   (2017-04-01)". The most important part is the "Annotation Release"
   number, e.g. "105". The date is NCBI's release date. Shown below this
   line is the date when UCSC imported the data, which is not relevant
   for manuscripts. Note that an "Annotation release" is not a "RefSeq
   release" , a "RefSeq release" is only about sequences, not their
   mapping to the genome. NCBI provides a list of `all current
   annotation
   releases <https://www.ncbi.nlm.nih.gov/genome/annotation_euk/all/>`__.
   The first annotation release for every genome is usually "100".

What is CCDS?
-------------

The `Consensus Coding Sequence
Project <https://www.ncbi.nlm.nih.gov/projects/CCDS/CcdsBrowse.cgi>`__
is a list of transcript coding sequence (CDS) genomic regions that are
identically annotated by RefSeq and Ensembl/GENCODE. CCDS undergoes
extensive manual review and you can consider these a subset of either
gene track, filtered for high quality. The CCDS identifiers are very
stable and allow you to link easily between the different databases. As
the name implies, it does not cover UTR regions or non-coding
transcripts.

How can I show a single transcript per gene?
--------------------------------------------

For the tracks "`UCSC
Genes <../cgi-bin/hgTrackUi?db=hg19&g=knownGene>`__" (hg19) or "`GENCODE
Genes <../cgi-bin/hgTrackUi?db=hg38&g=knownGene>`__" (hg38), click on
their title and on the configuration page, uncheck the box "Show splice
variants". Only a single transcript will be shown. The method for how
this transcript is selected is described in the next section below and
in the track documentation.

.. image:: ../images/SpliceVariants.png
   :alt: Changing splice variants
   :class: text-center
   :width: 750px

For the various single-transcript options of "NCBI RefSeq", please see
the discussion of "single transcript" tracks in the next section.

How can I download a file with a single transcript per gene?
------------------------------------------------------------

This is a common request, but very often this is not necessary when
designing an analysis. You will have to make a choice of this single
transcript using some mechanism, and this choice will affect your
pipeline results. It may be easier to keep all transcripts. For example,
instead of annotating enhancers with the closest "best-transcript", you
can annotate them with the closest exon of any transcript. When mapping
variants to transcripts, you can map to all transcripts and and show the
transcript with the worst impact first. When segmenting the chromosomes
into gene loci, you can use the union of all transcripts of a gene,
adding some predefined distance, rather than selecting a single "best"
transcript.

That being said, the main gene tracks have tables that try to show the
"best" transcript per gene. There are many choices, depending on the
assembly and the gene track and every selection method has a different
aim. For the knownGene tracks (UCSC genes on hg19, Gencode on hg38 and
mm10), data tables called "knownCanonical" were built at UCSC. For both
Gencode/Ensembl and RefSeq, the NCBI/EBI project MANE selects for each
gene the most relevant transcript, as long as these are identical
between Gencode and RefSeq. For NCBI RefSeq, the track RefSeqSelect also
selects the most relevant transcript(s) for each gene and is not limited
to transcripts that are identical between RefSeq and Ensembl. Therefore,
the following gene tracks have "best-transcripts" tracks:

**UCSC Genes on hg19**: For hg19, the knownCanonical table is a subset
of the `UCSC Genes <../cgi-bin/hgTrackUi?db=hg19&g=knownGene>`__ track.
It was generated at UCSC by identifying a canonical isoform for each
cluster ID, or gene. Generally, this is the longest isoform. It can be
downloaded directly from the `hg19 downloads
database <http://hgdownload.soe.ucsc.edu/goldenPath/hg19/database/>`__
or by using the `Table Browser <../cgi-bin/hgTables>`__.

**Gencode on hg38/mm10 - knownCanonical**: For hg38, the knownCanonical
table is a subset of the `GENCODE
v29 <../cgi-bin/hgTrackUi?db=hg38&g=knownGene>`__ track. It was
generated at UCSC. As opposed to the hg19 knownCanonical table, which
used computationally generated gene clusters and generally chose the
longest isoform as the canonical isoform, the hg38 table uses ENSEMBL
gene IDs to define clusters (that is to say, one canonical isoform per
ENSEMBL gene ID), and the method of choosing the isoform is described as
such:

*knownCanonical identifies the canonical isoform of each cluster ID or
gene using the ENSEMBL gene IDs to define each cluster. The canonical
transcript is chosen using the APPRIS principal transcript when
available. If no APPRIS tag exists for any transcript associated with
the cluster, then a transcript in the BASIC set is chosen. If no BASIC
transcript exists, then the longest isoform is used.*

It can be downloaded directly from the `hg38 downloads
database <http://hgdownload.soe.ucsc.edu/goldenPath/hg38/database/>`__
or by using the `Table Browser <../cgi-bin/hgTables>`__.

**NCBI RefSeq (hg19/hg38)**: This track collection contains three
subtracks that select the most relevant transcript for all or a subset
of genes, with slightly different aims:

-  RefSeq Select: NCBI manually selects few, usually one, transcript per
   gene called "RefSeq Select", based on `a lot of
   criteria <https://www.ncbi.nlm.nih.gov/refseq/refseq_select/>`__. The
   criteria include manual curation, whether a transcript appears in LRG
   sequences, whether it is well conserved and many more. Example use
   cases are comparative genomics and variant reporting. This subset is
   available in the RefSeq Select track under NCBI RefSeq.
-  MANE: RefSeq and the EBI also select one transcript for every protein
   coding gene that is annotated exactly the same in both Gencode and
   RefSeq, a project called `"MANE
   select" <https://www.ncbi.nlm.nih.gov/refseq/MANE/>`__, which is
   another subtrack of NCBI RefSeq. "MANE select" can be considered a
   subset of RefSeq Select.
-  HGMD: For the special case of clinical diagnostics where an even more
   reduced number of transcripts simplifies visual inspection, we
   provide another subtrack, "RefSeq HGMD". It contains (usually) a
   single transcript only for genes known to cause human genetic
   diseases and the transcript is the one to which all reported HGMD
   clinical variants can be mapped to. This transcript set is also a
   good choice for variant reporting.

This is rather complicated. Can you tell me which gene transcript track I should use?
-------------------------------------------------------------------------------------

For automated analysis, if you are doing NGS analysis and you need to
capture all possible transcripts, GENCODE provides one of the most
comprehensive gene sets. For human genetics or variant annotation, a
more restricted transcript set is usually sufficient and "NCBI RefSeq"
is the standard. If you are only interested in protein-coding
annotations, CCDS or UniProt may be an option, but this is rather
unusual. If you are interested in the best splice site coverage, AceView
is worth a look.

For manual inspection of exon boundaries of a single gene, and
especially if it is a transcript that is repetitive or hard to align
(e.g. very small exons), look at the UCSC RefSeq track and watch for
differences between the NCBI and UCSC exon placement. You can also BLAT
the transcript sequence. Manually look at ESTs, mRNAs, TransMap and
possibly Augustus, Genscan, SIB, SGP or GeneId in obscure cases where
you are looking for hints on what an alternative splicing could look
like.

You may also find the `Gene
Support <http://genome.ucsc.edu/s/view/GeneSupport>`__ public session
helpful. This session is a collection of tracks centered around
supporting evidence for genes.

Does UCSC provide GTF/GFF files for gene models?
------------------------------------------------

We provide files in GTF format, which is an extension to GFF2, for most
assemblies. More information on GTF format can be found `in our
FAQ <FAQformat.html#format4>`__.

These files are generated for four gene model tables: ncbiRefSeq,
refGene, ensGene, knownGene. Certain assemblies, such as hg19, will have
all four files while smaller assemblies may only have one or two of
these. Which file a user should use depends on their analysis, as they
contain different data and metadata.

These files are generated using the ``genePredToGtf`` method described
in our `downloads
FAQ <https://genome.ucsc.edu/FAQ/FAQdownloads.html#download37>`__ using
the ``-utr`` flag. They can be found on the download server address
*http://hgdownload.soe.ucsc.edu/goldenPath/$db/bigZips/genes/* where
*$db* is the assembly of interest. For example, the `hg38 GTF
files <http://hgdownload.soe.ucsc.edu/goldenPath/hg38/bigZips/genes/>`__.

.. |Turning on comprehensive gene set| image:: ../images/ComprehensiveSet.png
   :class: text-center
   :width: 750px
