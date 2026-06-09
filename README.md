# CredAlign
Adaptive Local Sequence Alignment Integrating Amino Acid Confidence

# Overview
De novo peptide sequencing is a key technology for discovering the dark matter of the cancer proteome, yet its output sequences often contain erroneous amino acid sites that severely hinder downstream biological source tracing. Existing local sequence alignment algorithms treat all sites equally without distinguishing between high- and low-confidence regions, allowing erroneous sites to obtain high scores through random matches, thereby misleading the selection of optimal alignment paths. To address this issue, we propose CredAlign, an adaptive local sequence alignment algorithm that incorporates amino acid confidence. It directly embeds the confidence score of each site into the amino acid match scoring function, and adaptively amplifies the contribution of high-confidence sites while suppressing interference from low-confidence ones via a linear weighting mechanism. Compared with the unweighted mode, CredAlign achieves significantly higher amino acid recall across nine distinct testing scenarios, with the improvement positively correlating with the proportion of erroneous sites in the query sequences. In practical applications, CredAlign successfully corrects two misalignments caused by low-confidence segments and identifies novel peptides encoded by the human RNF40, SPAG1, and RAI1 genes in HCT116 cells. These results validate the effectiveness of incorporating amino acid confidence into alignment scoring, and this mechanism can be integrated into other advanced alignment algorithms to improve their interpretation of the biological origins of de novo sequenced peptides for cancer dark matter discovery.
<div align="center">
  <img src="![Figure1](https://github.com/user-attachments/assets/a4379a9a-b264-4c56-9a76-c79c3aeada05)" 
       width="70%" 
       style="border: 1px solid #eee; border-radius: 5px;"/>
</div>
<p align="center">
  Figure 1. Amino acid confidence-weighted scoring mechanism of the CredAlign algorithm..
</p>

