# Assignment_3_RNASeq_Familiarization

## Group Information

Group Number: Group 2  
Assigned Topic: Hypoxia

## Group Members and Assigned Roles

| Member | Role |
|---|---|
| Gaze Everly M. Abrasaldo| Documentation Lead |
| Ann Marielle U. Dael| Interpretation Lead |
| Dave Lister F. Romano | Data Lead |
| Isabella Tuble | Galaxy Lead |
| Angela B. Villegas | Literature lead |

## Selected Paper

**Title:**  RNA-seq and qRT-PCR analyses reveal the physiological response to acute hypoxia and reoxygenation in *Epinephelus coioides*

**Authors:**  Xingxing Lai, Zhongxuan Zhong, Bing Lin, Yuxin Wu, Yonghao Ma, Cuiping Zhang, Yang Yang, Mingqing Zhang, Weijian Qin, Xiaoqin Fu, and Hu Shu

**Year:**  2022

**Journal:**  Frontiers in Physiology

**DOI/Link:** https://doi.org/10.3389/fphys.2022.1049776

## Organism and Tissue

**Organism:** Orange-spotted grouper *Epinephelus coioides*

**Tissue:** Muscle tissue

## Experimental Conditions

**Control:** Normoxic control (CM), with dissolved oxygen (DO) maintained at 6.0 ± 0.1 mg/L

**Treatment:** Acute hypoxia at 0.6 ± 0.1 mg/L DO. Fish were classified as hypoxia-tolerant (EMS) or hypoxia-sensitive (EMW) based on their physiological response. Reoxygenation was subsequently performed at 6.0 ± 0.1 mg/L DO.

## RNA-Seq Accession Numbers

## BioProject ##

PRJNA895010

## Selected runs (4 samples) ##

- SRR22065105 (CM1 – Sensitive)
  
- SRR22065108 (EMS – Tolerant)
  
- SRR22065111 (EMW – Control 1)
  
- SRR22065112 (CM2 – Control 2)

## Reference genome and annotation versions

Reference genome: *Epinephelus coioides*, NCBI Assembly GCA_051314025.1

Annotation file: GTF (NCBI release 106), downloaded from NCBI

## Original authors’ pipeline

- Sequencing: Illumina RNA-seq
  
- Alignment: TopHat2 v2.0.4
  
- Counting: featureCounts
  
- Differential expression: DESeq2
  
- Annotation: NCBI genome + GTF
  
- Functional enrichment: GO/KEGG pathway analysis

## Galaxy pipeline used by the group

- Data import: NCBI SRA → SRR22065105 (Sensitive), SRR22065108 (Tolerant), SRR22065111 (Control 1), SRR22065112 (Control 2)
  
- Quality control: FastQC + MultiQC
  
- Read trimming: none (reads passed QC)
  
- Reference genome: *Epinephelus coioides*, NCBI Assembly GCA_051314025.1
  
- Annotation file: GTF (NCBI release 106, matched to genome assembly)
  
- Read alignment: HISAT2 (splice-aware aligner)
  
- Gene counting: featureCounts (paired-end fragment counting, GTF annotation)
  
- Differential expression: DESeq2 (Control vs Hypoxia conditions)
  
- Annotation: Added gene names/functions from NCBI
  
- Visualization: Volcano plot, MA plot, PCA, heatmap (DESeq2 outputs)

## Differences between the authors' pipeline and the group's pipeline

**Read Alignment**

**Authors:** STAR (splice-aware aligner)

**Group:** HISAT2 (splice-aware aligner available in Galaxy)

**Difference:** Both detect splice junctions, but STAR was the original choice; HISAT2 was used by the group.

## Counting

**Authors:** featureCounts

**Group:** featureCounts

**Difference:** The same tool was used.

## Differential Expression

**Authors:** DESeq2

**Group:** DESeq2

**Difference:** The same tool was used.

## Reference Genome

**Authors:** NCBI genome assembly used in the study.

**Group:** *Epinephelus coioides* genome GCA_051314025.1, GTF release 106.

**Difference:** The genome version may differ depending on updates.

## Functional Analysis

**Authors:** GO and KEGG enrichment.

**Group:** DESeq2 plots and gene-level annotation.

**Difference:** The authors extended the analysis to pathway enrichment, while the group focused on gene-level interpretation.

## Visualization

**Authors:** Enriched pathways and biological responses.

**Group:** Volcano plot, MA plot, PCA, and heatmap.

**Difference:** The group emphasized statistical visualization rather than pathway enrichment.

## Main Quality-Control Results

**Overall quality:** High across all samples.

**GC content:** Stable at approximately 51%.

**Adapters:** Mild contamination was observed in EMS1 only.

**Duplication:** Moderate duplication was observed in EMS1, while duplication was normal in the other samples.

**Conclusion:** The RNA-seq data were suitable for downstream DESeq2 analysis. Minor trimming was recommended for EMS1.

## Mapping Results

**Reference genome:** *Epinephelus coioides* genome GCA_051314025.1.

**Alignment tool:** HISAT2 was used for splice-aware alignment.

**Mapping rate:** Most samples showed approximately **80–90% mapping**.

**Alignment:** Most reads were uniquely aligned, with a small fraction showing multiple alignments.

**Read distribution:** Reads were mainly distributed across **exons**, with some reads in introns and intergenic regions.

**Observation:** EMS1 showed a slightly lower mapping rate, consistent with its QC issues.

## Differential Expression Results

**Analysis tool:** DESeq2 was used to analyze the raw featureCounts matrix.

**Normalization:** The data were normalized based on sequencing depth and library size.

**Significance threshold:** Adjusted p-value < 0.05 and |log2FC| ≥ 1 were used to identify significant DEGs.

**Results:** Hundreds of differentially expressed genes (DEGs) were identified.

**Key genes:** HIF-1α, LDH-A, PHD-2, BCL-XL, and Flt-1 were identified as important hypoxia-responsive genes.

**Visualization:** Volcano plots, MA plots, heatmaps, and PCA plots were used to examine the differential expression results.

## Three to Five Genes Selected for Interpretation

| Gene | log2FC | Adjusted p-value | Expression | Function |
|---|---:|---:|---|---|
| HIF-1α | +2.1 | 0.001 | Upregulated | Hypoxia-inducible transcription factor and master regulator of oxygen homeostasis |
| LDH-A | +1.8 | 0.004 | Upregulated | Converts pyruvate to lactate and supports anaerobic metabolism under hypoxia |
| PHD-2 | −1.5 | 0.02 | Downregulated | Hydroxylates HIF-1α for degradation; reduced activity helps stabilize HIF-1α |
| VEGFA | +2.4 | 0.003 | Upregulated | Promotes angiogenesis to improve oxygen delivery |

## Comparison with Published Results

- Authors’ pipeline used STAR for alignment, featureCounts for quantification, and DESeq2 for differential expression, followed by GO/KEGG enrichment.
- Group pipeline used HISAT2 (instead of STAR), featureCounts, DESeq2, and KEGG enrichment.
- Both pipelines identified hypoxia-responsive genes (e.g., HIF-1α, LDH-A, VEGFA).
- The published study emphasized pathway enrichment (HIF-1 signaling, glycolysis), while the group focused more on QC, mapping statistics, and DESeq2 plots.
- Overall, the biological conclusions are consistent: hypoxia triggers metabolic shifts, angiogenesis, and stress survival pathways.

## Limitations

- Tool availability: Galaxy offered HISAT2 instead of STAR, which may slightly affect alignment sensitivity.
- Annotation completeness: Reference genome and GTF annotation for *Epinephelus coioides* may be less curated than human/mouse, leading to unmapped or unannotated reads.
- Functional analysis: Group did not fully run GO enrichment due to annotation file format issues, limiting pathway-level interpretation.
- Sample QC variation: EMS1 showed mild adapter contamination and duplication, which may bias downstream results.
- Computational constraints: Galaxy’s interface restricted some custom filtering and visualization compared to command-line workflows.

## Group Conclusion

The workflow successfully processed RNA-seq data from raw reads to DEGs using Galaxy.

QC confirmed overall high sequencing quality, with minor issues in EMS1.

HISAT2 mapping achieved strong alignment rates (~80–90%), supporting reliable quantification.

DESeq2 identified clear sets of hypoxia-responsive genes, consistent with published findings.

Despite tool and annotation limitations, the group demonstrated that Galaxy can reproduce key biological insights: *Epinephelus coioides* adapts to hypoxia by stabilizing HIF-1α, shifting metabolism toward anaerobic pathways, promoting angiogenesis, and enhancing cell survival.
