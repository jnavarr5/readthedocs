.. container:: encodeHeader

   |ENCODE Project at UCSC| ENCODE Resources and Frequently Asked
   Questions

.. container:: wrapper

   .. container:: bar

      .. rubric:: About
         :name: about
         :class: title

   .. container:: content

      During the first decade of the ENCODE project (2003-2014), UCSC
      coordinated all project data, hosting genome browser tracks and
      download files for all Consortium experiments. UCSC also developed
      tools for locating and accessing ENCODE data as well as outreach
      and tutorial materials to help the user community. The *ENCODE
      Data at UCSC* resources below are those developed during this
      period. For newer data and outreach materials, consult the *ENCODE
      Project* section.

.. container:: wrapper

   .. container:: bar

      .. rubric:: ENCODE Project Resources
         :name: encode-project-resources
         :class: title

   .. container:: content

      -  `ENCODE Portal
         (encodeproject.org) <http://encodeproject.org/ENCODE/>`__
      -  `ENCODE Project at NHGRI
         (genome.gov) <http://genome.gov/10005107>`__
      -  `Nature ENCODE Explorer <http://www.nature.com/encode/>`__ and
         `Galaxy Biomedical Tools <https://main.g2.bx.psu.edu/>`__
      -  `ENCODE Data at
         GEO <https://www.ncbi.nlm.nih.gov/geo/info/ENCODE.html>`__
      -  `ENCODE Data at
         Ensembl <http://www.ensembl.org/info/website/tutorials/encode.html>`__

.. container:: wrapper

   .. container:: bar

      .. rubric:: Helpful Resources for ENCODE Data at UCSC
         :name: helpful-resources-for-encode-data-at-ucsc
         :class: title

   .. container:: content

      -  `Tutorials and User's Guide </ENCODE/usageResources.html>`__
      -  `Track and File Search </ENCODE/search.html>`__
      -  **Human:** `Experiment
         Matrix </ENCODE/dataMatrix/encodeDataMatrixHuman.html>`__,
         `Experiment List </ENCODE/dataSummary.html>`__,
         `Downloads </ENCODE/downloads.html>`__ and `Cell
         Types </ENCODE/cellTypes.html>`__
      -  **Mouse:** `Experiment
         Matrix </ENCODE/dataMatrix/encodeDataMatrixMouse.html>`__,
         `Experiment List </ENCODE/dataSummaryMouse.html>`__,
         `Downloads </ENCODE/downloadsMouse.html>`__ and `Cell
         Types </ENCODE/cellTypesMouse.html>`__
      -  `ENCODE Antibodies </ENCODE/antibodies.html>`__ and `ENCODE
         Registered Experiment Variables </ENCODE/otherTerms.html>`__
      -  `File Formats </ENCODE/fileFormats.html>`__ and `Data
         Standards </ENCODE/dataStandards.html>`__ and `Software
         Tools </ENCODE/softwareTools.html>`__
      -  `UCSC Genome Browser FAQ Page <../../FAQ/>`__ and `Searchable
         Google Groups Mailing
         List <http://groups.google.com/a/soe.ucsc.edu/group/genome?hl=en>`__

      Search all ENCODE web pages at UCSC:  
      Search the entire UCSC Genome Browser website:  

.. container:: wrapper

   .. container:: bar

      .. rubric:: ENCODE at UCSC Frequently Asked Questions
         :name: encode-at-ucsc-frequently-asked-questions
         :class: title

   .. container:: content

      DATA FILE AND TABLE FORMAT QUESTIONS
      `How do I extract information about an ENCODE experiment from the
      filename? <#release6>`__
      `What is the difference between a file xxx and the related file
      xxxV2? <#release5>`__
      `How do I learn more about different ENCODE file
      formats? <#release7>`__
      `What does xxx mean in a file in
      hgdownload/encodeDCC/hg19/wgEncode(track)? <#release15>`__
      `How do I download ENCODE histone data in BED
      format? <#release9>`__
      `How do I find the meaning of a column of a BED
      file? <#release11>`__
      `What is the definition of "score" in ENCODE
      tables? <#release8>`__
      `How are the columns signalValue and peak calculated in narrowPeak
      files? <#release18>`__
      `What does the name column represent for DNase clustered BED
      files? <#release10>`__
      `Can I convert WIG files into a variableStep format to use with
      SitePro? <#release14>`__
      `How do I learn more about peak calling algorithms used to
      generate narrowPeak and broadPeak files? <#release19>`__
      `What program reads ".bb" TFBS files from ENCODE? <#release20>`__
      OTHER QUESTIONS
      `How do I display ENCODE data from GEO in the genome
      browser? <#release0>`__
      `Where can I find ENCODE papers? <#release13>`__
      `Is there a service providing ENCODE data on a hard
      drive? <#release12>`__
      `May I use the the ENCODE figure from your
      homepage? <#release17>`__
      `Which cell types are used by ENCODE? <#release1>`__
      `Which cell protocols were used in my track of
      interest? <#release16>`__
      `Where can I find the ENCODE growth protocol for a specific cell
      type? <#release2>`__
      `Has transcription factor xxx been mapped by
      ENCODE? <#release3>`__
      `How do I find overlaps between my own ChIP-seq regions and
      available ENCODE transcription factors? <#release4>`__
      `I am making a public hub for my paper, is there an example html
      file to use for my data description? <#release21>`__
      `Questions and feedback welcome </ENCODE/contacts.html>`__.

.. container:: wrapper

   |image1|

   .. container:: bar

      .. rubric:: GEO DATA
         :name: geo-data
         :class: title

   .. container:: content

      | **Question:**
      | How do I display ENCODE data from GEO in the genome browser?

      | **Response:**
      | Please avoid loading GEO data as a custom track! Rather, as
        nearly all ENCODE data at GEO are already hosted as tracks on
        the UCSC browser, load the existing corresponding track.

      Take note of the GEO sample accession (GSM) number and enter it
      into the Track Search tool accessible from the left side of the
      ENCODE portal page by clicking `Search </ENCODE/search.html>`__,
      for example
      `GSM999240 <../../cgi-bin/hgTracks?db=hg19&hgt_tSearch=1&tsCurTab=simpleTab&tsSimple=GSM999240>`__.
      Or use the Advanced Track Search page and select "GEO sample
      accession" from the pull down menu displaying "Cell, tissue or DNA
      sample". Click the box next to your track resulting from the
      search and the "View in Browser" button.

      If you have data that is not already in the browser we recommend
      converting your BED files to `bigBed
      format <../../goldenPath/help/bigBed.html>`__. You could download
      our source tools for converting from BED to bigBed (as described
      in the previous link) or use the tools at the
      `Galaxy <http://galaxyproject.org/>`__ website. For questions
      regarding Galaxy you will have to contact them directly.

.. container:: wrapper

   |image2|

   .. container:: bar

      .. rubric:: ENCODE CELL TYPES
         :name: encode-cell-types
         :class: title

   .. container:: content

      | **Question:**
      | Which cell types are used by ENCODE?

      | **Response:**
      | On the left side of the `ENCODE portal page </ENCODE/>`__ under
        **Human** and **Mouse** are links to the cell types used in all
        ENCODE experiments.

.. container:: wrapper

   |image3|

   .. container:: bar

      .. rubric:: ENCODE PROTOCOLS
         :name: encode-protocols
         :class: title

   .. container:: content

      | **Question:**
      | Where can I find the ENCODE growth protocol for a specific cell
        type? For example RCC 7860?

      | **Response:**
      | To find a specific protocol, for example for human RCC 7860
        cells, from the ENCODE portal navigate to the `Human Cell
        Types </ENCODE/cellTypes.html>`__ page. Under the "Documents"
        column for RCC 7860, click the link to connect to see the growth
        protocol named after the lab that provided the document, in this
        case "Crawford".

      Another path to ENCODE protocols is from the link
      `/ENCODE/protocols/ </ENCODE/protocols>`__. Navigate to the cell
      protocols and then human directories to find the link to the same
      RCC 7860 protocol file as linked on the above `Human Cell
      Types </ENCODE/cellTypes.html>`__ page.

      If you have further questions about a protocol contact the lab
      that registered the protocol.

.. container:: wrapper

   |image4|

   .. container:: bar

      .. rubric:: TRANSCRIPTION FACTORS
         :name: transcription-factors
         :class: title

   .. container:: content

      | **Question:**
      | Has transcription factor xxx been mapped by ENCODE?

      | **Response:**
      | A quick way to view the list of transcription factors mapped by
        ENCODE is to view the ChIP-seq matrix for either
        `human </ENCODE/dataMatrix/encodeChipMatrixHuman.html>`__ or
        `mouse </ENCODE/dataMatrix/encodeChipMatrixMouse.html>`__.
        Targets are listed horizontally across the top, indicating
        available mapped transcription factor data. Clicking on the
        green highlighted boxes will bring you to experiment data
        specific to the corresponding cell type and target.

      Another option is to use the `Track
      Search <../../cgi-bin/hgTracks?db=hg19&hgt_tSearch=1&tsCurTab=advancedTab>`__
      or `File Search <../../cgi-bin/hgFileSearch>`__ tools and to
      search the "Antibody or target protein" field to see if the
      desired transcription factor is listed.

.. container:: wrapper

   |image5|

   .. container:: bar

      .. rubric:: MAPPING A CUSTOM TRACK TO TRANSCRIPTION FACTORS
         :name: mapping-a-custom-track-to-transcription-factors
         :class: title

   .. container:: content

      | **Question:**
      | How do I find overlaps between my own ChIP-seq regions and
        available ENCODE transcription factors?

      | **Response:**
      | By using the `Table Browser tool <../../cgi-bin/hgTables>`__ you
        can add your ChIP-seq information as a custom track and then use
        the "intersection" feature to intersect the Txn Factor ChIP
        track table listed under the Regulation group with your custom
        track. Note, your custom track should contain ChIP-seq regions
        in BED format, for more information visit our `custom
        tracks <../../goldenPath/help/customTrack.html>`__ page.

      If you are unfamiliar with the Table Browser, please refer to our
      `help page <../../goldenPath/help/hgTablesHelp.html>`__ and the
      section on `intersecting
      data <../../goldenPath/help/hgTablesHelp.html#Intersection>`__.

.. container:: wrapper

   |image6|

   .. container:: bar

      .. rubric:: FILES NAMED xxxV2
         :name: files-named-xxxv2
         :class: title

   .. container:: content

      | **Question:**
      | What is the difference between a file xxx and the related file
        xxxV2? Why is the xxx file not displayed in the browser?

      | **Response:**
      | For files named similar to xxxV2, often the "V2" refers to a
        second version that revokes earlier versions that are therefore
        not displayed in the browser. Revoked files are still available
        for download, but they will be indicated as "replaced " or
        "revoked" in the related metadata file named "files.txt" present
        in the corresponding download directory.

.. container:: wrapper

   |image7|

   .. container:: bar

      .. rubric:: ENCODE METADATA AND FILENAMES
         :name: encode-metadata-and-filenames
         :class: title

   .. container:: content

      | **Question:**
      | How do I extract information about an ENCODE experiment from the
        filename?

      | **Response:**
      | This is not recommended. While ENCODE filenames have some
        metadata embedded, the information there is not complete nor
        easily extracted. Rather, use the file's metadata, for example
        in "files.txt", or access metadata in the following places:

      The metadata uses controlled vocabulary (cv.ra), which can be
      downloaded as a text file
      `here <http://hgdownload.soe.ucsc.edu/goldenPath/encodeDCC/cv.ra>`__.

.. container:: wrapper

   |image8|

   .. container:: bar

      .. rubric:: ENCODE FILE FORMATS
         :name: encode-file-formats
         :class: title

   .. container:: content

      | **Question:**
      | How do I learn more about different ENCODE file formats? For
        example what is the difference between a file.bed and a
        file.bed9 in the ENCODE methylation data?

      | **Response:**
      | By clicking the `File Formats <../../ENCODE/fileFormats.html>`__
        link from the ENCODE portal page you can reach a list of various
        file formats used in ENCODE. Every ENCODE file has metadata
        included under a "files.txt" file in the related downloads page.
        For example, from the `HudsonAlpha DNA methylation download
        page <http://hgdownload.soe.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeHaibMethylRrbs/>`__,
        in the
        `files.txt <http://hgdownload.soe.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeHaibMethylRrbs/files.txt>`__
        file, a line after the specific bed9 file in question,
        wgEncodeHaibMethylRrbsAg04449UwstamgrowprotSitesRep1.bed9, reads
        'objstatus=replaced'. This metadata indicates this bed9 file was
        preliminary data that has since been replaced. A similar note in
        the automatically displayed README file states: "WARNING -
        Revoked and replaced data files may be present in this
        directory."

.. container:: wrapper

   |image9|

   .. container:: bar

      .. rubric:: ENCODE SCORE DEFINITION
         :name: encode-score-definition
         :class: title

   .. container:: content

      | **Question:**
      | What is the definition of "score" in ENCODE tables?

      | **Response:**
      | The score (between 0-1000) determines how darkly an item is
        displayed in the browser (with 1000 being black). The darkness
        of an item's box is proportional to the maximum signal strength
        observed in any cell line.

      To find out exactly how score has been calculated for a specific
      track, contact the lab that created the data. There are often
      several links to authors' labs in the credits section for each
      track at the bottom of a track's description page.

.. container:: wrapper

   |image10|

   .. container:: bar

      .. rubric:: ENCODE DATA IN BED FORMAT
         :name: encode-data-in-bed-format
         :class: title

   .. container:: content

      | **Question:**
      | How do I download ENCODE histone data in BED format? From the
        Table Browser I can select to download the file in BED format,
        but I am limited to just a few thousand lines. When I looked in
        the ENCODE Downloads directory I could only find the path to a
        bigWig file, for example
        wgEncodeBroadHistoneGm12878H3k27acStdSig for human build hg19.

      | **Response:**
      | The ENCODE BED files you are looking to download are the 'peak
        calls', which are in the extended broadPeak or narrowPeak
        formats, described `here <../../FAQ/FAQformat.html#ENCODE>`__.
        For example, within the database mentioned (H3K27ac histone mark
        in GM12878 cells) there is a BED representation in the file:
        "wgEncodeBroadHistoneGm12878H3k27acStdPk.broadPeak.gz". Using
        the `File Search <../../ENCODE/search.html>`__ tool you can use
        the setting "Data Format: Peaks Broad" to narrow your results to
        only these types of files.

.. container:: wrapper

   |image11|

   .. container:: bar

      .. rubric:: ENCODE BED FILE FORMAT
         :name: encode-bed-file-format
         :class: title

   .. container:: content

      | **Question:**
      | What does the name column represent for DNase clustered BED
        files? I downloaded the ENCODE BED file
        wgEncodeRegDnaseClustered.bed from the DNase footprinting assay.
        However, I am having trouble understanding the 4th column in
        this file. Usually this column, as I understand from the file
        format FAQ page, is assigned to name.

      | **Response:**
      | For the DNase cluster BED files, the name field represents the
        number of items in the cluster. To find out more information
        about each cluster, you can click on the item in the browser
        image and it will take you to a details page that will list all
        of the items in the cluster and the cell lines.
        `Here <../../cgi-bin/hgc?db=hg19&c=chr21&o=33032260&t=33033430&g=wgEncodeRegDnaseClustered&i=58&l=33032260&r=33033430>`__
        is an example of a details page for a DNase item on chromosome
        21. There are 58 items in this cluster and you can see the name
        value is 58.

.. container:: wrapper

   |image12|

   .. container:: bar

      .. rubric:: ENCODE ChIP-seq BED FILES
         :name: encode-chip-seq-bed-files
         :class: title

   .. container:: content

      | **Question:**
      | How do I find the meaning of a column of a BED file? I have
        downloaded ENCODE Chip-Seq BED files that have the following
        format:

      chr21 9825311 9827738 . 1000 . 4.51792 256.60845 261.34671 1809

      What is the meaning of the information from the fourth field
      forward?

      | **Response:**
      | ENCODE has a number of `ENCODE-specific
        formats <../../FAQ/FAQformat.html#ENCODE>`__. ENCODE ChIP-seq
        files are typically stored in the ENCODE
        `narrowPeak <../../FAQ/FAQformat.html#format12>`__ format. This
        format extends BED6 to include fields for signalValue, two
        measurements of statistical significance (pValue and qValue),
        and the offset of a single base 'point source' peak within the
        region. The dots are used for name and strand which are not
        applicable.

.. container:: wrapper

   |image13|

   .. container:: bar

      .. rubric:: DOWNLOAD ALL ENCODE DATA
         :name: download-all-encode-data
         :class: title

   .. container:: content

      | **Question:**
      | Is there a service providing ENCODE data on a hard drive? What
        is the total data volume? We have been trying FTP, but it takes
        too much bandwidth and time.

      | **Response:**
      | The total volume of ENCODE data are greater than 31 TB.
        Unfortunately, it is not possible for you to obtain a disk copy,
        however, there is a new protocol to try called UDR (UDT Enabled
        Rsync). UDR provides users much faster download rates.

      Here is an example using UDR, once installed, to download all the
      mouse mm9 ENCODE information:

      .. code:: code

         $ udr rsync -avP hgdownload.soe.ucsc.edu::goldenPath/mm9/encodeDCC/ /my/local/mm9/

      Please read more about the new UDR method
      `here <../../ENCODE/newsarch.html#091213>`__.
      For those not downloading high amounts of data, we highly
      recommend using rsync. For example:

      .. code:: code

         $ rsync -a -P rsync://hgdownload.soe.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeDir/wgEncodeFile ./

      Using rsync has the advantage of starting up where it left off
      after a failure, when run again.

.. container:: wrapper

   |image14|

   .. container:: bar

      .. rubric:: ENCODE PAPERS
         :name: encode-papers
         :class: title

   .. container:: content

      | **Question:**
      | Where can I find ENCODE papers? I would like a list of the
        principal ENCODE Papers, can you send a link to a list of a core
        30 papers detailing ENCODE's results?

      | **Response:**
      | References to the ENCODE analysis publications of September 2012
        can be found here: `ENCODE Analysis Package
        Publications </ENCODE/analysis.html#tools>`__. There is also a
        comprehensive set of ENCODE-related publications listed on the
        `Publications page </ENCODE/pubs.html>`__ linked on the left
        side of the `ENCODE portal page </ENCODE/>`__.

.. container:: wrapper

   |image15|

   .. container:: bar

      .. rubric:: CONVERTING WIG FILES TO VARIABLESTEP
         :name: converting-wig-files-to-variablestep
         :class: title

   .. container:: content

      | **Question:**
      | Can I convert WIG files into a variableStep format to use with
        SitePro? I am trying to use a tool called SitePro within
        Cistrome. This tool uses WIG and BED files to compute score
        profiles on the BED regions. I have downloaded, through
        Cistrome/Galaxy, the ENCODE WIG files which have BED-like
        structure:

      chr1 3002700 3002800 0.17

      However, this WIG file's BED-like structure is not accepted by
      SitePro. Is there a way to format the WIG files as variablestep
      and not BED-like?

      | **Response:**
      | There is not a way to convert formats using the Genome Browser
        directly, but you could convert formats using a script. There is
        an example script in our genomewiki,
        `here <http://genomewiki.ucsc.edu/index.php/Wiggle_BED_to_variableStep_format_conversion>`__.

.. container:: wrapper

   |image16|

   .. container:: bar

      .. rubric:: UNIQUE ENCODE DATA DETAILS
         :name: unique-encode-data-details
         :class: title

   .. container:: content

      | **Question:**
      | What does xxx mean in a file in
        hgdownload/encodeDCC/hg19/wgEncode(track)? For example
        downloadable files in the wgEncodeCaltechRnaSeq/ directory have
        a gene_id format like gene_id "GM12878-rep1.1045777" where the
        first part is the cell type. Would you know what does the last
        number 1045777 means?

      | **Response:**
      | At the top of the page for each of the download directories you
        are visiting there is a README.txt file that is automatically
        displayed. A link is provided that will bring you to a user
        interface enabling filtering of files by cell type and other
        parameters, as well as including additional information such as
        release status, restriction dates, track description, methods,
        and metadata that can answer such questions.

      For example in the README.txt file displayed at the top of the
      page in the `Caltech RNA-seq
      directory <http://hgdownload.soe.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeCaltechRnaSeq/>`__
      you can find the following link:
      "http://genome.ucsc.edu/cgi-bin/hgFileUi?db=hg19&g=wgEncodeCaltechRnaSeq"

      By navigating to the page above, `Caltech RNA-seq Downloadable
      Files <../../cgi-bin/hgFileUi?db=hg19&g=wgEncodeCaltechRnaSeq>`__,
      you can scroll to the bottom (or click the "Description" link in
      the top right corner) and read the track description's "Methods"
      section. In the "Data Processing and Analysis" section there is
      information explaining how the numbers in gene_id,
      "GM12878-rep1.####" represent de novo identifiers output by
      Cufflinks software. At the very bottom of the page is a "Credits"
      section where contacts are listed. You should send remaining
      process-specific questions about the data you are investigating to
      the appropriate contact listed.

.. container:: wrapper

   |image17|

   .. container:: bar

      .. rubric:: ENCODE PROTOCOLS
         :name: encode-protocols-1
         :class: title

   .. container:: content

      | **Question:**
      | Which cell protocols were used in my track of interest? Did the
        Open Chromatin ENCODE tracks use standard ENCODE cell protocols?

      | **Response:**
      | Standard growth protocols were used for all ENCODE experiments,
        including the Open Chromatin ENCODE tracks. A directory of all
        ENCODE protocols is available here:
        `http://genome.ucsc.edu/ENCODE/protocols/ </ENCODE/protocols>`__.

.. container:: wrapper

   |image18|

   .. container:: bar

      .. rubric:: ENCODE GRAPHIC
         :name: encode-graphic
         :class: title

   .. container:: content

      | **Question:**
      | May I use the the ENCODE figure from your homepage? I am writing
        my PhD thesis and I would like to use it in both electronic and
        printed form.

      | **Response:**
      | The `ENCODE graphic </ENCODE/aboutScaleup.html>`__ displaying
        how investigators employ a variety of assays and methods to
        identify functional elements can be used in publications as long
        as credit is given. Please credit Ian Dunham at EBI and Darryl
        Leja at NHGRI as noted below the image.

.. container:: wrapper

   |image19|

   .. container:: bar

      .. rubric:: ENCODE TABLE SCHEMA
         :name: encode-table-schema
         :class: title

   .. container:: content

      | **Question:**
      | How are the columns signalValue and peak calculated in
        narrowPeak files? For example, I want more information about UW
        Histone "wgEncodeUwHistone...PkRep1.narrowPeak" files.

      | **Response:**
      | The `File Format FAQ <../../FAQ/FAQformat.html>`__ provides
        explanations about various file formats. Also a file's related
        Track Description page may include important information, such
        as the `UW
        Histone <../../cgi-bin/hgTrackUi?db=hg19&g=wgEncodeUwHistone>`__
        "Methods section", which describes how data were processed to
        produce peaks. In the "Credits" section there is also a lab
        contact. To request further information for UW Histone data, for
        example, you could contact the lab to learn more about the peak
        calling algorithm or other methods involved.

      When using the `Table Browser <../../cgi-bin/hgTables>`__ there is
      a "describe table schema" button that gives information similar to
      that located in the File Format FAQ, plus the related Track
      Description.

      For example with settings "group: Regulation", "track: UW
      Histone", and "table: wgEncode...PkRep#", if you click the
      "describe table schema" button you will find definitions for
      signalValue and peak. Scrolling down you will find the related
      Track Description for UW Histone with the explanation for peak
      calling under "Methods" and the laboratory contact under
      "Credits".

.. container:: wrapper

   |image20|

   .. container:: bar

      .. rubric:: ENCODE SOFTWARE TOOLS
         :name: encode-software-tools
         :class: title

   .. container:: content

      | **Question:**
      | How do I learn more about peak calling algorithms used to
        generate `narrowPeak <../../FAQ/FAQformat.html#format12>`__ and
        `broadPeak <../../FAQ/FAQformat.html#format13>`__ files?

      | **Response:**
      | An excellent resource to review is the ENCODE Software Tools
        page, located on the lefthand side of the `ENCODE
        portal </ENCODE/>`__ under "Software Tools." Click through to
        the `Software Tools Used to Create the ENCODE
        Resource </ENCODE/encodeTools.html>`__ and here you can find
        references for the various peak calling algorithms under
        "ChIP-seq Peak Callers".

      By visiting various ENCODE tracks such as `HAIB
      TFBS <../../cgi-bin/hgTrackUi?db=hg19&g=wgEncodeHaibTfbs>`__,
      `SYDH
      TFBS <../../cgi-bin/hgTrackUi?db=hg19&g=wgEncodeSydhTfbs>`__, or
      `UW
      Histone <../../cgi-bin/hgTrackUi?db=hg19&g=wgEncodeUwHistone>`__
      you can learn more about the processes each lab used to generate
      peaks, and pick a method suitable for your data. Since these data
      were not generated by the UCSC Browser group, questions about the
      data methods need to be directed to the corresponding lab. Under
      the "Credits" section you will find a contact for further
      questions left unanswered by reading the descriptions.

.. container:: wrapper

   |image21|

   .. container:: bar

      .. rubric:: ENCODE FILES
         :name: encode-files
         :class: title

   .. container:: content

      | **Question:**
      | What program reads ".bb" TFBS files from ENCODE? I am interested
        in looking at the AWG TFBS data. I downloaded the files and one
        is called:
        spp.optimal.wgEncodeBroadHistoneGm12878CtcfStdAlnRep0_VS_wgEncodeBroadHistoneGm12878ControlStdAlnRep0.bb

      However, I do not have a program that can open this file. What is
      the program for this file and where can I find it?

      | **Response:**
      | Files ending in ".bb" are
        `bigBed <../../FAQ/FAQformat.html#format1.5>`__ files. Click
        `here <../../goldenPath/help/bigBed.html>`__ for extensive
        information on the bigBed format and how to extract data with
        different binary utilities located in this
        `directory <http://hgdownload.soe.ucsc.edu/admin/exe/>`__.

.. container:: wrapper

   |image22|

   .. container:: bar

      .. rubric:: HUB EXAMPLES
         :name: hub-examples
         :class: title

   .. container:: content

      | **Question:**
      | I am making a public hub for my paper, is there an example html
        file to use for my data description?

      | **Response:**
      | The browser's `public hubs <../../cgi-bin/hgHubConnect?>`__
        provide excellent examples of hub documentation. Here are two
        examples of track description pages from the ENCODE Analysis
        hub:

      | http://ftp.ebi.ac.uk/pub/databases/ensembl/encode/integration_data_jan2011/hg19/uniformTfbs.html
        http://ftp.ebi.ac.uk/pub/databases/ensembl/encode/integration_data_jan2011/hg19/uniformRNA.html

      **Useful tips when writing your track descriptions:**
      It is best to assume a broad audience of students as well as
      researchers. Spelling out common acronynms, for example, may be
      useful for those who are new to genomics.
      The paper's abstract may be a good start for your track's
      "Description" section.
      Provide as much detail as possible in the "Methods" section.
      A email address must be prominently displayed for questions
      relating to the track.
      | **Other Examples:**

      Here are a few good examples of hub structure and configuration
      from the ENCODE Analysis hub:

      | http://ftp.ebi.ac.uk/pub/databases/ensembl/encode/integration_data_jan2011/hub.txt
      | http://ftp.ebi.ac.uk/pub/databases/ensembl/encode/integration_data_jan2011/genomes.txt
      | http://ftp.ebi.ac.uk/pub/databases/ensembl/encode/integration_data_jan2011/hg19/trackDb.txt

      Note: We recommend a minimal number of default visible tracks in
      your trackDb.txt to quicken hub loading time and to avoid
      overwhelming users. For more suggestions on hub structure, please
      see our `Public Hub
      Guidelines <http://genomewiki.soe.ucsc.edu/index.php/Public_Hub_Guidelines>`__
      wikipage. Also, for help defining unfamiliar terms, you may want
      to see the Hub Track Database Definition's `table of
      contents <http://genome.ucsc.edu/goldenPath/help/trackDb/trackDbHub.html#toc>`__.

Updated 15 August 2014

.. |ENCODE Project at UCSC| image:: /images/gbLogoOnly.png
   :target: /ENCODE/index.html
.. |image1| image:: ../../images/top.gif
   :target: #FAQ
.. |image2| image:: ../../images/top.gif
   :target: #FAQ
.. |image3| image:: ../../images/top.gif
   :target: #FAQ
.. |image4| image:: ../../images/top.gif
   :target: #FAQ
.. |image5| image:: ../../images/top.gif
   :target: #FAQ
.. |image6| image:: ../../images/top.gif
   :target: #FAQ
.. |image7| image:: ../../images/top.gif
   :target: #FAQ
.. |image8| image:: ../../images/top.gif
   :target: #FAQ
.. |image9| image:: ../../images/top.gif
   :target: #FAQ
.. |image10| image:: ../../images/top.gif
   :target: #FAQ
.. |image11| image:: ../../images/top.gif
   :target: #FAQ
.. |image12| image:: ../../images/top.gif
   :target: #FAQ
.. |image13| image:: ../../images/top.gif
   :target: #FAQ
.. |image14| image:: ../../images/top.gif
   :target: #FAQ
.. |image15| image:: ../../images/top.gif
   :target: #FAQ
.. |image16| image:: ../../images/top.gif
   :target: #FAQ
.. |image17| image:: ../../images/top.gif
   :target: #FAQ
.. |image18| image:: ../../images/top.gif
   :target: #FAQ
.. |image19| image:: ../../images/top.gif
   :target: #FAQ
.. |image20| image:: ../../images/top.gif
   :target: #FAQ
.. |image21| image:: ../../images/top.gif
   :target: #FAQ
.. |image22| image:: ../../images/top.gif
   :target: #FAQ
