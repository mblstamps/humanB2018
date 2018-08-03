
Code for denoising 

--i-demultiplexed-seqs demux.qza \
>  --o-table table.qza \
>  --o-representative-sequences rep-seqs \
> --o-denoising-stats stats.qza\
>  --p-trim-left-f 0 \
>  --p-trim-left-r 0 \
>  --p-trunc-len-f 230 \
>  --p-trunc-len-r 155 \
>  --p-n-threads 0 \
>  --verbose
