# Annotations for the PI-CAI Challenge: Public Training and Development Dataset

## Reference
Please cite the following article, if you are using the PI-CAI: Public Training and Development Dataset:

	A. Saha, J. J. Twilt, J. S. Bosma, B. van Ginneken, D. Yakar, M. Elschot, J. Veltman, J. J. Fütterer, M. de Rooij, H. Huisman, "Artificial Intelligence and Radiologists at Prostate Cancer Detection in MRI: The PI-CAI Challenge", DOI: 10.5281/zenodo.6522364

	@ARTICLE{PICAI_BIAS,
    	author    = {Anindo Saha, Jasper J. Twilt, Joeran S. Bosma, Bram van Ginneken, Derya Yakar, Mattijs Elschot, Jeroen Veltman, Jurgen Fütterer, Maarten de Rooij, Henkjan Huisman},
    	title     = {{Artificial Intelligence and Radiologists at Prostate Cancer Detection in MRI: The PI-CAI Challenge}}, 
    	year      = {2022},
        doi       = {10.5281/zenodo.6522364}
    }


## License
[CC-BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)


## Imaging Dataset
For the description of the associated imaging data, see [Zenodo](https://zenodo.org/record/6517398).

## Annotations
Patient cases used for the training datasets of PI-CAI are annotated with the same reference standard as used for the [ProstateX challenge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6228312/pdf/JMI-005-044501.pdf), i.e. histologically-confirmed ([ISUP] ≥ 2) positives, and histologically- ([ISUP][ISUP] ≤ 1) or MRI- ([PI-RADS][PI-RADS] ≤ 2) confirmed negatives, without follow-up.

For all cases, csPCa lesions are delineated and/or csPCa outcomes are recorded, by one of 10 trained investigators or 1 radiology resident, under supervision of one of 3 expert radiologists, at RUMC, UMCG or NTNU. For all training cases, automated AI-derived delineations of csPCa lesions [(Bosma et al., 2022)][Bosma22] have also been made available.

The following annotations are provided:

| Location                       | Description         |
|-----------------------------|-----------------|
| [csPCa_lesion_delineations/<br>human_expert/original/](csPCa_lesion_delineations/human_expert/original/) | Original csPCa annotations, as made by one of the trained investigators or radiology resident. |
| [csPCa_lesion_delineations/<br>human_expert/resampled/](csPCa_lesion_delineations/human_expert/resampled/) | Original csPCa annotations resampled to the associated axial T2-weighted scan. |
| [csPCa_lesion_delineations/<br>AI/Bosma22a/](csPCa_lesion_delineations/AI/Bosma22a/) | Automated AI-derived delineations of csPCa lesions [(Bosma et al., 2022)][Bosma22]. |

### Label Mapping


| Label                       | Meaning         |
|-----------------------------|-----------------|
| 1                           | ISUP ≥ 2 (AI-derived)  |
| 2                           | ISUP 2          |
| 3                           | ISUP 3          |
| 4                           | ISUP 4          |
| 5                           | ISUP 5          |


### Stats
The table below provides an overview of the number of patients, cases and lesions in the PI-CAI: Public Training and Development Dataset. These numbers include both voxel-level delineated cases (1295/1500, 86%) and case-level recorded lesion outcomes (205/1500, 14%).

|                             |                 |
|-----------------------------|-----------------|
| No. of Patients             | 1476            |
| No. of Cases                | 1500            |
| — Benign or Indolent PCa    | 1075            |
| — csPCa (ISUP ≥ 2)          | 425             |
| No. of ISUP-Based Lesions   | 456             |
| — ISUP 2                    | 260             |
| — ISUP 3                    | 109             |
| — ISUP 4                    | 41              |
| — ISUP 5                    | 55              |


## Managed By
Diagnostic Image Analysis Group,
Radboud University Medical Center,
Nijmegen, The Netherlands

## Contact Information
- Anindo Saha: Anindya.Shaha@radboudumc.nl
- Jasper Twilt: Jasper.Twilt@radboudumc.nl
- Joeran Bosma: Joeran.Bosma@radboudumc.nl
- Henkjan Huisman: Henkjan.Huisman@radboudumc.nl

[PI-RADS]: https://www.europeanurology.com/article/S0302-2838(19)30180-0/fulltext
[ISUP]: https://pubmed.ncbi.nlm.nih.gov/27150257/
[Bosma22]: https://fastmri.eu/research/bosma22a.html
