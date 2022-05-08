# Annotations for the [PI-CAI Challenge](https://pi-cai.grand-challenge.org/): Public Training and Development Dataset

### Imaging Dataset
To download the associated imaging data, visit: [https://zenodo.org/record/6517398](https://zenodo.org/record/6517398).
Note, the **Public Training and Development Dataset** of the [PI-CAI challenge](https://pi-cai.grand-challenge.org/) includes 328 cases from the [ProstateX challenge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6228312/pdf/JMI-005-044501.pdf). Thus, we strongly recommend using this dataset exclusively, and not in addition to the ProstateX dataset.  

### Reference Standard for Annotations
Patient cases used for the training datasets of the [PI-CAI challenge](https://pi-cai.grand-challenge.org/) are annotated with the same reference standard as used for the [ProstateX challenge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6228312/pdf/JMI-005-044501.pdf), i.e. histologically-confirmed ([ISUP] ≥ 2) positives, and histologically- ([ISUP][ISUP] ≤ 1) or MRI- ([PI-RADS][PI-RADS] ≤ 2) confirmed negatives, without follow-up. Note, this means that certain patients (e.g. `11054`) can have a prior study that was found to be negative (`1001074` in 2018), but a subsequent study that was found to be positive (`1001075` in 2020). In this case, each study is annotated with respect to its associated histopathology or radiology findings only. From our institutional findings at [RUMC](https://www.diagnijmegen.nl/) ([Venderink et al., 2019](https://bjui-journals.onlinelibrary.wiley.com/doi/full/10.1111/bju.14853)), such scenarios typically emerge for less than <1% negative cases.

For all cases, csPCa lesions are delineated and/or csPCa outcomes are recorded, by one of 10 trained investigators or 1 radiology resident, under supervision of one of 3 expert radiologists, at [RUMC](https://www.diagnijmegen.nl/) or [UMCG](https://www.umcg.nl/). Automated AI-derived delineations of csPCa lesions ([Bosma et al., 2022][Bosma22]) and the prostate whole-gland ([see algorithm used for this task](https://grand-challenge.org/algorithms/prostate-segmentation/)), will also be made available.

### Annotations and Resources
| Location                    | Description         |
|-----------------------------|-----------------|
| [csPCa_lesion_delineations/<br>human_expert/original/](csPCa_lesion_delineations/human_expert/original/) | Original csPCa annotations, as made by one of the trained investigators or radiology resident. |
| [csPCa_lesion_delineations/<br>human_expert/resampled/](csPCa_lesion_delineations/human_expert/resampled/) | Original csPCa annotations resampled to the spatial resolution of the associated axial T2-weighted scan. |
| [csPCa_lesion_delineations/<br>AI/Bosma22a/](csPCa_lesion_delineations/AI/Bosma22a/) | Automated AI-derived delineations of csPCa lesions ([Bosma et al., 2022a][Bosma22]) *{to-be-released}*. |
| [anatomical_delineations/whole_gland/<br>AI/Bosma22b/](anatomical_delineations/whole_gland/AI) | Automated AI-derived delineations of the prostate whole-gland ([see algorithm used for this task](https://grand-challenge.org/algorithms/prostate-segmentation/)) *{to-be-released}*. |
| [clinical_information/<br>marksheet.csv/](clinical_information/marksheet.csv/) | Clinical information (patient age, PSA, PSA density, prostate volume) and overview of each study (e.g. MRI vendor and scanner, [GS](https://www.cancer.gov/publications/dictionaries/cancer-terms/def/gleason-score) per lesion if biopsies or prostatectomy was performed) in this dataset. |


### Label Mapping of [csPCa Annotations](csPCa_lesion_delineations/) 
Note, all [expert-derived csPCa annotations](csPCa_lesion_delineations/human_expert/) carry **granular or multi-class labels** (ISUP ≤ 1, 2, 3, 4, 5), while all [automated AI-derived annotations](csPCa_lesion_delineations/AI/) carry **binary labels** (ISUP ≤ 1 or ≥ 2).

| Label                       | [Expert-Derived Annotations](csPCa_lesion_delineations/human_expert/) | [AI-Derived Annotations](csPCa_lesion_delineations/AI/) |
|:---------------------------:|:---------------------:|:---------------------:|
| 0                           | ISUP ≤ 1              | ISUP ≤ 1              |
| 1                           | N/A                   | ISUP ≥ 2              |
| 2                           | ISUP 2                | N/A                   |
| 3                           | ISUP 3                | N/A                   |
| 4                           | ISUP 4                | N/A                   |
| 5                           | ISUP 5                | N/A                   |


### Dataset Characteristics
The table below provides an overview of the number of patients, cases and lesions in the PI-CAI: Public Training and Development Dataset. These numbers include both voxel-level delineated cases (1295/1500, 86%) and case-level recorded lesion outcomes (205/1500, 14%).

| Characteristic              | Frequency       |
|:----------------------------|:---------------:|
| No. of Patients             | 1476            |
| No. of Cases                | 1500            |
| — Benign or Indolent PCa    | 1075            |
| — csPCa (ISUP ≥ 2)          | 425             |
| No. of ISUP-Based Lesions   | 456             |
| — ISUP 2                    | 260             |
| — ISUP 3                    | 109             |
| — ISUP 4                    | 41              |
| — ISUP 5                    | 55              |


### Reference
If you are using this dataset or some part of it, please cite the following article:

● [A. Saha, J. J. Twilt, J. S. Bosma, B. van Ginneken, D. Yakar, M. Elschot, J. Veltman, J. J. Fütterer, M. de Rooij, H. Huisman, "Artificial Intelligence and Radiologists at Prostate Cancer Detection in MRI: The PI-CAI Challenge", DOI: 10.5281/zenodo.6522364](https://zenodo.org/record/6522364#.YnessuhBy2Q)

**BibTeX:**
```
@ARTICLE{PICAI_BIAS,
    author = {Anindo Saha, Jasper J. Twilt, Joeran S. Bosma, Bram van Ginneken, Derya Yakar, Mattijs Elschot, Jeroen Veltman, Jurgen Fütterer, Maarten de Rooij, Henkjan Huisman},
    title  = {{Artificial Intelligence and Radiologists at Prostate Cancer Detection in MRI: The PI-CAI Challenge}}, 
    year   = {2022},
    doi    = {10.5281/zenodo.6522364}
}
```

### License
[CC-BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

### Managed By
Diagnostic Image Analysis Group,
Radboud University Medical Center,
Nijmegen, The Netherlands

### Contact Information
- Anindo Saha: Anindya.Shaha@radboudumc.nl
- Jasper Twilt: Jasper.Twilt@radboudumc.nl
- Joeran Bosma: Joeran.Bosma@radboudumc.nl
- Henkjan Huisman: Henkjan.Huisman@radboudumc.nl

[PI-RADS]: https://www.europeanurology.com/article/S0302-2838(19)30180-0/fulltext
[ISUP]: https://pubmed.ncbi.nlm.nih.gov/27150257/
[Bosma22]: https://fastmri.eu/research/bosma22a.html

