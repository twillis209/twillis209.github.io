# GWS loci in fcFDR analysis

Using the GWS threshold of 5e-8, I found 17 loci with a v-value below threshold. However, quite a few of the lead SNPs at these loci had high PID p-values. Were we doing cFDR, these would not have met a typical threshold of, say, 1e-4, for inclusion in the fitting process and would have had their v-value defaulted to 1. 

| CHR38 |      BP38 | SNPID       |     v.ra | ALT_FREQ |    P.pid |   |
|-------|-----------|-------------|----------|----------|----------|---|
|     1 | 113630788 | rs1230666   | 2.97e-12 |    0.139 | 1.11e-01 |   |
|     1 | 172746562 | rs78037977  | 4.74e-08 |    0.118 | 3.79e-03 |   |
|    10 |   6059828 | rs12722490  | 7.50e-09 |    0.030 | 1.44e-02 |   |
|    10 |   8059464 | rs3781094   | 4.14e-08 |    0.365 | 4.86e-02 |   |
|    12 |  55991020 | rs705699    | 4.32e-08 |    0.390 | 4.19e-01 |   |
|    16 |  11005850 | rs7194305   | 9.23e-12 |    0.409 | 2.75e-06 |   |
|    16 |  28965699 | rs7500321   | 3.03e-08 |    0.261 | 1.75e-01 |   |
|    17 |  39747478 | rs2941519   | 3.48e-11 |    0.492 | 1.19e-02 |   |
|    18 |  12818923 | rs80262450  | 7.65e-14 |    0.089 | 9.31e-07 |   |
|    19 |  10381598 | rs144309607 | 2.38e-08 |    0.031 | 1.67e-01 |   |
|     2 |  60933484 | rs13026755  | 1.53e-08 |    0.343 | 7.95e-05 |   |
|     2 | 191079016 | rs11889341  | 1.82e-08 |    0.229 | 3.66e-02 |   |
|     2 | 203874196 | rs3087243   | 9.26e-09 |    0.470 | 1.38e-01 |   |
|    21 |  42434957 | rs1893592   | 4.57e-08 |    0.276 | 3.43e-01 |   |
|     4 | 122109428 | rs114237393 | 1.66e-08 |    0.080 | 6.48e-04 |   |
|     5 |  10690637 | rs5745271   | 1.22e-08 |    0.407 | 1.95e-02 |   |
|     6 |  90267049 | rs72928038  | 3.46e-08 |    0.180 | 1.65e-01 |   |

Of those SNPs with a p-value less than 0.01, we have the following:

| CHR38 |      BP38 | SNPID       |     v.ra | ALT_FREQ |    P.pid | gene_name | local_genes                                                             |
|-------|-----------|-------------|----------|----------|----------|-----------|-------------------------------------------------------------------------|
|     1 | 172746562 | rs78037977  | 4.74e-08 |    0.118 | 3.79e-03 |           | FASLG                                                                   |
|    16 |  11005850 | rs7194305   | 9.23e-12 |    0.409 | 2.75e-06 | CLEC16    | CIITA, DEXI, RP11-876N24.3, RP11-876N24.7, RP11-876N24.5, RP11-876N24.4 |
|    18 |  12818923 | rs80262450  | 7.65e-14 |    0.089 | 9.31e-07 | PTPN2     | PSMG2, RP11-973H7.5, RP11-973H7.4, Y_RNA, RP11-973H7.1                  |
|     2 |  60933484 | rs13026755  | 1.53e-08 |    0.343 | 7.95e-05 |           | LINC01185, RPL21P33, REL, RNU4-51P, RP11-373L24.1                       |
|     4 | 122109428 | rs114237393 | 1.66e-08 |    0.080 | 6.48e-04 |           | AC097533.1, RN7SL335P                                                   |

Thaventhiran et al. conducted both common (MAF > 0.05) and intermediate frequency (MAF > 0.0005, though you might disagree that is an 'intermediate' frequency interval) GWAS in their AD-PID cohort. The former detected no GWS loci and the latter only a missense variant in TNFRSF13B (TACI), which has been previously identified in CVID. Although the authors did not make it easy to determine the provenance of the data deposited in the EBI GWAS catalogue (Guille's source, I assume), I have found out that they comprise the intermediate frequency GWAS summary statistics. 

Thaventhiran performed a fixed effect meta-analysis of their AD-PID intermediate frequency GWAS with a MAF > 0.01 GWAS of CVID by Li et al. (2015), which turned up the MHC and a variant in CLEC16A as GWS loci. Suggestive loci were seen in the EOMES promoter and proximal to PTPN2. 

The second and third plots below show our recovering the same signals in CLEC16A and PTPN2, albeit at different SNPs; in particular, our lead SNP is inside PTPN2, whereas the meta-analysis SNP was between PSMG2 and PTPN2. I did not want to read too much into these things about the identity of the SNP, though; wouldn't we have to perform fine-mapping to get down to the causal variant?

![](/images/120521/zoomed/rs78037977_chr1:172246562-173246562.png)

CLEC16A variant

![](/images/120521/zoomed/rs7194305_chr16:10505850-11505850.png)

PTPN2 variant

![](/images/120521/zoomed/rs80262450_chr18:12318923-13318923.png)

![](/images/120521/zoomed/rs13026755_chr2:60433484-61433484.png)

![](/images/120521/zoomed/rs114237393_chr4:121609428-122609428.png)



