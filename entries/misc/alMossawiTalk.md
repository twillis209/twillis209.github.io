# 'Unpicking pathogenic responses in human spondyloarthritis', Dr Hussein Al-Mossawi, Oxford, 23/3/21

Director of immunology research at UCB, a biotech/pharma company.
  
## Introduction 

PhD was in ankylosing spondyloarthritis, moved to psoriatic arthritis. 

Talk is about an experiment that began four years ago on treatment-naive olig. PsA using aspirated synovial fluid, broken down into three stories and four methods:

- scRNA-seq
- ATAC-seq immune subset-specific (was not actually discussed)
- CyTOF
- bulk transcriptomics (to validate the preceding efforts)

Began work wanting to look at transcriptome and TCR alpha/beta sequences, but only way to do this at the time was with Smart-seq2, plate-based and too expensive, but then 10X Genomics brought out their droplet-based platform (lab was first to do it in Oxford).
  
## Single-cell interrogation of psoriatic arthritis synovial fluid

(Work done with Frank Penkava, Nature Comms, 2020)

Began looking at cellular landscape of PsA using CyTOF. Saw large expansion of memory CD8+ cells compared to PsA blood. PsA is associated with polymorphisms in MHCI genes, but wanted to know if there were self-peptides to which the T-cells were reacting, so wanted to sequence TCRs (see alpha/beta sequences comment above).

Took fresh sorted CD8+ and CD4+ cells. Sequenced using 10X platform to build a map of what the T-cell compartment looked like ('maps' presented were t-SNE and UMAP). Began by trying to identify different T cell helper subsets like Tregs, Th17 (these are implicated in disease as blocking IL-17 [something] helps in this disease). To their surprise, didn't find many cells making IL-17.

On the one hand, single-cell clustering is quite subjective, but did their best to label 'clusters' based on expression of marker genes. Felt could not confidently call clusters due to ambiguity between cell types and cell states.

Pulled in expanded CD8 population cells from tissue/PBMC? with help of Newcastle-based collaborator after criticism in first round of reviews. Found that synovial fluid showed evidence of cells with high expression of granzymes, perforins, other effectors.

Also evidence of clonal expansion in SF compared with tissue. Compared PBMC and SFMC TCR usage. In UMAP, see that clonality sits around two populations, 'HLA-DR8 high' (?) and another group. Finding is that clonal cells appear to be proliferating in the joint. In the CD4+ population, saw most of the clonality sitting around the Treg area.

[Paper is Penkava et al. Nature Comms 2020]

Validated 10X with Smart-seq2, the latter picked out the same clone, overlapped nicely.

Is a given CD8 alpha-beta clone in one cell state/type or do they exist in multiple clusters? SFMC CD8+ enriched clones were present in multiple clusters as seen in the UMAP projection.

Are these clones recognising similar or very distinct antigens? Used the work of Glanville et al. (2018) which provided an 'glyph' (sp?) algorithm to look at CDRs, strip away nucleotide diversity, and determine the key differing amino acids and how they align. Very different V-betas could see something very similar in terms of peptide primary structure (I think those cells seeing the same thing are 'convergence groups'). Looking at their own data from three patients, they found several convergence groups ~ uniformly distributed over the patients.

The TCR convergence groups were dominated by specific clusters with the majority having the TRM phenotype (ZNF683+/'hobbit'). Others were 'cucling' or occupied the HLA-DR high CD8 state. When one looks at what these CD8+ cells in convergence groups are expressing vs. other cells in the synovial fluid, they showed high expression of granzymes, other effectors again.

Then asked how these cells in clusters and convergence groups differ from their 'cluster mates' who are not in the same convergence group. Those in the convergence groups looked 'more activated', had more highly expressed effectors, cell trafficking genes, pro-inflammatory genes. Cells in convergence group in PBMC sample also showed higher expression of trafficking genes. Cells in the synovial fluid showed higher expression of chemokine receptors associated with migration/trafficking into the joint. CXCR3 may play a role in this process and has been targeted by some in pharma for inhibition.

From questions: why are these cells proliferating in the joint? Probably not due to some CMV peptide in the joint (for example).

Some patients who receive anti-cancer immunotherapy (e.g. PD1 blocker) go on to develop rheumatoid factor-negative arthritis (I did not know this). This set of patients may be an interesting cohort to study to the end of understanding the aetiology of rheumatoid arthritis.
 
## Exploring synovial Treg function in SpA (comparing with PsA and AS)

(Work with Davide Simone, under review.)

SpA sees expansion of Tregs in synovial fluid like in JIA, other rheumatic diseases, and inflamed tissue in general.

Took Tregs from PsA clustering described above and broke down into sub-type clustered. Validated with the use of cells from AS (?) and recapitulated subtype clusters.

Looked at functional specialisation of Treg subsets and found a subset expressing cytotoxic genes (CD8+ ?).

Comparing SpA Tregs in PBMC and SF, found that reactome pathways in SF were enriched for interferon and TCR signalling, coheres with idea of stimulation in the joint compartment.

Looked at LAG-3+ Tregs to determine role of LAG-3 in this setting. LAG-3 is expressed an activated T-cells as a 'checkpoint'. CD161 and CD8 Tregs preferentially express LAG-3. Can LAG-3 mediate 'reverse signalling' from Tregs?

Took LPS-stimulated monocytes and found that LAG-3-Fc suppressed their inflammatory function. Suggested that LAG-3 engagement with MHCII(?) could reverse inflammatory stimulation.

Notes in summary that CD8+ Tregs are relatively neglected, in particular their expression of LAG-3 and its capacity to signal to the myeloid compartment.
   
## Focus on functional PsA myeloid compartment using CyTOF (rushed through this)

(Nicole Yager, on Biorxiv).

What are the cell types in the joint in PsA and what are they making?

Took synovial fluid and incubated with protein transport inhibitors at time 0. Wanted to find which intracellular proteins that could be determined ex vivo.

PsA and healthy control blood samples are hard to distinguish. Main takeaway of cellular composition analysis is large expansion of macrophage subset in PsA SF (not in blood). Comparing HC and PsA blood and PsA SF, found expansion of monocyte, intermediate monocyte, dendritic cell subsets.

Also used CyTOF to validate TRM cells in PsA SF as found in scRNA-seq discussed above.

Then performed ex vivo functional characterisation of SF cells in PsA at times 0 and 6h with unsupervised clustering. Found upregulation of osteopontin, CCL2, and IL-8. Use of 3' scRNA-seq, confirmed upregulation of SPP1 in the myeloid compartment. Did not find upregulation of IL-17, which is interesting as IL-17 blockade shows clinical benefit, but apparently not due to action in the joint.
