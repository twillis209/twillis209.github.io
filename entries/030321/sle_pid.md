# PID conditioned on SLE

There was an interesting peak on chromosome 6 in this data set in the plot we looked at last week, but this was probably because I accidentally left the MHC in the `sle_pid` data set (the same code worked on three other data sets). 

![](/images/030321/sle_pid_backToBack.png)

I identified peaks on:
* chromosome 2
* chromosome 6
* chromosome 16 (two distinct ones)

![](/images/030321/sle_pid_backToBack_chr2_6_16.png)

## Chromosome 2

The SNP in STAT4 is newly genome-wide significant in `cfdr`.

![](/images/030321/sle_pid_backToBack_chr2_190_5M-191_5M.png)

## Chromosome 6

I don't believe the signal here is actually distinct from the MHC.

![](/images/030321/sle_pid_backToBack_chr6_22M-28_5M.png)

## Chromosome 16

CLEC16A was genome-wide significant in the AD-PID meta-analysis in Thaventhiran et al. but not in the original AD-PID GWAS. This locus became GWS using `cfdr` but not `fcfdr`. 

I also took a closer look at the almost-GWS SNP near IRF8, which was not GWS in the original AD-PID GWAS (not sure about the meta-analysis).

![](/images/030321/sle_pid_backToBack_chr16_10M-12_5M.png)
![](/images/030321/sle_pid_backToBack_chr16_85M-87_5M.png)
