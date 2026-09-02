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


