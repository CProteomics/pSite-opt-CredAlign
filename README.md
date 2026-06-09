# CredAlign
Adaptive Local Sequence Alignment Integrating Amino Acid Confidence

# Overview
De novo peptide sequencing is a key technology for discovering the dark matter of the cancer proteome, yet its output sequences often contain erroneous amino acid sites that severely hinder downstream biological source tracing. Existing local sequence alignment algorithms treat all sites equally without distinguishing between high- and low-confidence regions, allowing erroneous sites to obtain high scores through random matches, thereby misleading the selection of optimal alignment paths. To address this issue, we propose CredAlign, an adaptive local sequence alignment algorithm that incorporates amino acid confidence. It directly embeds the confidence score of each site into the amino acid match scoring function, and adaptively amplifies the contribution of high-confidence sites while suppressing interference from low-confidence ones via a linear weighting mechanism. Compared with the unweighted mode, CredAlign achieves significantly higher amino acid recall across nine distinct testing scenarios, with the improvement positively correlating with the proportion of erroneous sites in the query sequences. In practical applications, CredAlign successfully corrects two misalignments caused by low-confidence segments and identifies novel peptides encoded by the human RNF40, SPAG1, and RAI1 genes in HCT116 cells. These results validate the effectiveness of incorporating amino acid confidence into alignment scoring, and this mechanism can be integrated into other advanced alignment algorithms to improve their interpretation of the biological origins of de novo sequenced peptides for cancer dark matter discovery.
![Figure 1. Amino acid confidence-weighted scoring mechanism of the CredAlign algorithm.](images/CredAlign.tif)
<div align="center">
  <img src="[CredAlign.tif](https://github.com/user-attachments/files/28736867/CredAlign.tif)" alt="Figure 1" width="70%" style="border: 1px solid #eee; border-radius: 5px;">
</div>
<p align="center">
  Figure 1. Amino acid confidence-weighted scoring mechanism of the CredAlign algorithm..
</p>

# System Requirements
.NET Runtime: .NET 6.0 (for C# components). Operating Systems: Windows 10/11.

# Usage
## 1. Input Preparation
Prepare the following input files and directories:
- **BLOSUM62 matrix**: Place standard BLOSUM62 scoring matrix files in `./Release/net6.0/BLOSUM62/`
- **Query sequences**:
  - Place one or more `.csv` files in `./Release/net6.0/Query/`
  - Each line in the CSV file represents one query sequence, formatted as:
    `Amino_acid_sequence,Amino_acid_confidence_scores`
  - Example: `LHFLTEPAEVNPGR,98.7612 97.42165 99.97832 99.83066 99.02905 99.61818 98.94964 37.70059 68.17488 22.33408 54.68313 61.94963 4.88969 96.74363`
- **Template sequences**:
  - Place one or more .csv files in `./Release/net6.0/Template/`
  - Each line in the CSV file represents one template sequence

Note: The program will perform pairwise local sequence alignment: **every query sequence against every template sequence automatically**.
## 2. Run CredAlign
Execute the program by double-clicking `CredAlign.exe` in `./Release/net6.0/`

After completion, all alignment results will be generated in: `./Release/net6.0/Result/`

## 3. Output Interpretation
 Each line represents a CredAlign alignment result with the following semicolon-separated format:
`Query:Query_sequence,Confidence_scores;Template:Template_sequence;CredAlign_Result:Aligned_query,Aligned_template,CIGAR_string`

 Example of a complete result line:
`Query:LHFLTEPAEVNPGR,98.7612 97.42165 99.97832 99.83066 99.02905 99.61818 98.94964 37.70059 68.17488 22.33408 54.68313 61.94963 4.88969 96.74363;
Template:PPRPPRP.PRQLLPVMQTLTSRIHFLTEPAEPAGAARAAQPCVMGNIQKKLTGKAEGGK;CredAlign_Result:
LHFLTEPAE.VNPGR(query),IHFLTEPAEPAGAAR(template),MMMMMMMMMDMMMMM(CIGAR)`

 The specific meanings of each field are:
 - **Query**: Input query sequence and its corresponding amino acid confidence scores
 - **Template**: Input template sequence used for alignment
 - **CredAlign_Result**:
   - Aligned query sequence (marked with `query`)
   - Aligned template sequence (marked with `template`)
   - Standard CIGAR string for alignment annotation (marked with `CIGAR`)
    
# Citing CredAlign
# Support
For questions or bug reports, please contact: hecuitongpro@163.com
