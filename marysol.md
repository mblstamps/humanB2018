These are my notes for our project:

Full data set from: https://www.mothur.org/wiki/MiSeq_SOP

Kozich JJ, Westcott SL, Baxter NT, Highlander SK, Schloss PD. (2013): Development of a dual-index sequencing strategy and curation pipeline for analyzing amplicon sequence data on the MiSeq Illumina sequencing platform. Applied and Environmental Microbiology. 79(17):5112-20.

Paper at: http://aem.asm.org/content/79/17/5112.full.pdf+html

Using Qiime2:

Data was put in MBL server 
directory /mnt/home/shared in workshop-server.qiim2.org
password: stamps2018

Import fastq files (no need for barcodes)-paired end
qiime tools import \
--type 'SampleData[PairedEndSequencesWithQuality]' \
--input-path MouseLongitudinal \ 
--source-format CasavaOneEightSingleLanePerSampleDirFmt \
--output-path demux-paired-end.qza

Make a qzv demus to pick where to cut off seqs
qiime demux summarize \
--i-data demux-paired-end.qza \
--o-visualization demux.qzv

Run DADA2 – truncate both forward and reverse separately
For server:
qiime dada2 denoise-paired \
 --i-demultiplexed-seqs demux.qza \
 --o-table table.qza \
 --o-representative-sequences rep-seqs \
--o-denoising-stats stats.qza\
 --p-trim-left-f 0 \
 --p-trim-left-r 0 \
 --p-trunc-len-f 230 \
 --p-trunc-len-r 155 \
 --p-n-threads 0 \
 --verbose

For my computer:
qiime dada2 denoise-paired \
 --i-demultiplexed-seqs demux.qza \
 --o-table table.qza \
 --o-representative-sequences rep-seqs \
--p-trim-left-f 0 \
 --p-trim-left-r 0 \
 --p-trunc-len-f 230 \
 --p-trunc-len-r 155 \
 --p-n-threads 0 \
 --verbose

