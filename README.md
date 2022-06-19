# Annotations for the [PI-CAI Challenge](https://pi-cai.grand-challenge.org/): Public Training and Development Dataset

### Imaging Dataset
To download the associated imaging data, visit: [https://zenodo.org/record/6517398](https://zenodo.org/record/6517398).
Note, the **Public Training and Development Dataset** of the [PI-CAI challenge](https://pi-cai.grand-challenge.org/) includes 328 cases from the [ProstateX challenge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6228312/pdf/JMI-005-044501.pdf). Thus, we strongly recommend using this dataset exclusively, and not in addition to the ProstateX dataset.  

### Reference Standard for Annotations
Patient cases used for the training datasets of the [PI-CAI challenge](https://pi-cai.grand-challenge.org/) were annotated with the same reference standard as used for the [ProstateX challenge](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6228312/pdf/JMI-005-044501.pdf), i.e. histologically-confirmed ([ISUP] ≥ 2) positives, and histologically- ([ISUP][ISUP] ≤ 1) or MRI- ([PI-RADS][PI-RADS] ≤ 2) confirmed negatives, without follow-up. Note, this means that certain patients (e.g. `11054`) can have a prior study that was found to be negative (`1001074` in 2018), but a subsequent study that was found to be positive (`1001075` in 2020). In this case, each study was annotated with respect to its associated histopathology or radiology findings only. From our institutional findings at [RUMC](https://www.diagnijmegen.nl/) ([Venderink et al., 2019](https://bjui-journals.onlinelibrary.wiley.com/doi/full/10.1111/bju.14853)), such scenarios typically emerge for less than <1% negative cases.

### Annotations and Resources
For all cases, csPCa lesions were delineated and/or csPCa outcomes were recorded, by one of 10 trained investigators or 1 radiology resident, under supervision of one of 3 expert radiologists, at [RUMC](https://www.diagnijmegen.nl/) or [UMCG](https://www.umcg.nl/). Lesion delineations were created using [ITK-SNAP v3.80](http://www.itksnap.org/pmwiki/pmwiki.php). 

Out of the 1500 cases shared in the [Public Training and Development Dataset](https://zenodo.org/record/6517398), 1075 cases have benign tissue or indolent PCa (i.e. their labels should be empty or full of 0s) and 425 cases have csPCa (i.e. [their labels should have lesion blobs of value 2, 3, 4 or 5](#label-mapping-of-cspca-annotations)). Out of these 425 positive cases, only 220 cases carry an annotation derived by a human expert. Remaining 205 positive cases have not been annotated. In other words, only 17% (220/1295) of the annotations provided in [picai_labels/csPCa_lesion_delineations/human_expert](csPCa_lesion_delineations/human_expert/) should have csPCa lesion annotations, while the remaining 83% (1075/1295) of annotations should be empty. 

Automated AI-derived delineations of the prostate whole-gland ([see algorithm used for this task](https://grand-challenge.org/algorithms/prostate-segmentation/)) has been made available. Automated AI-derived delineations of csPCa lesions ([Bosma et al., 2022][Bosma22]) will also be made available.

| Location                    | Description     |
|:----------------------------|:----------------|
| [csPCa_lesion_delineations/<br>human_expert/original/](csPCa_lesion_delineations/human_expert/original/) | Original csPCa annotations, as made by one of the trained investigators or radiology resident. Depending on the annotator/center and their preference, some of these annotations were mapped or created at the spatial resolution of the T2W image, while others have been created at the resolution of the ADC or DWI/HBV images. Either way, for every annotation in this folder, all lesion delineations will always clearly map to observations in DWI/ADC imaging. Available for 1295/1500 (86%) cases. |
| [csPCa_lesion_delineations/<br>human_expert/resampled/](csPCa_lesion_delineations/human_expert/resampled/) | Original csPCa annotations resampled to the spatial resolution of the associated axial T2-weighted scan. Available for 1295/1500 (86%) cases. |
| [csPCa_lesion_delineations/<br>AI/Bosma22a](csPCa_lesion_delineations/AI/Bosma22a) | Automated AI-derived delineations of csPCa lesions ([Bosma et al., 2022a][Bosma22]). |
| [anatomical_delineations/<br>whole_gland/AI/Bosma22b](anatomical_delineations/whole_gland/AI/Bosma22b) | Automated AI-derived delineations of the prostate whole-gland ([see algorithm used for this task](https://grand-challenge.org/algorithms/prostate-segmentation/)). Note, that AI-derived annotations can be susceptible to errors or faulty segmentations (e.g. whole-gland segmentation for case [`11050_1001070`](anatomical_delineations/whole_gland/AI/11050_1001070.nii.gz)). |
| [clinical_information/<br>marksheet.csv/](clinical_information/marksheet.csv/) | Clinical information (patient age, [PSA][PSA], [PSA density][PSA], prostate volume) and overview of each study (e.g. anonymized study date, MRI vendor and scanner used for acquisition, [GS][GS] per lesion {if prostatectomy or biopsies were performed}) in this dataset. |


### Label Mapping of [csPCa Annotations](csPCa_lesion_delineations/) 
All [expert-derived csPCa annotations](csPCa_lesion_delineations/human_expert/) carry **granular or multi-class labels** ([ISUP][ISUP] ≤ 1, 2, 3, 4, 5), while all [automated AI-derived annotations](csPCa_lesion_delineations/AI/) will carry **binary labels** ([ISUP][ISUP] ≤ 1 or ≥ 2).

| Label                       | [Expert-Derived Annotations](csPCa_lesion_delineations/human_expert/) | [AI-Derived Annotations](csPCa_lesion_delineations/AI/) |
|:---------------------------:|:---------------------:|:---------------------:|
| 0                           | [ISUP][ISUP] ≤ 1      | [ISUP][ISUP] ≤ 1      |
| 1                           | N/A                   | [ISUP][ISUP] ≥ 2      |
| 2                           | [ISUP][ISUP] 2        | N/A                   |
| 3                           | [ISUP][ISUP] 3        | N/A                   |
| 4                           | [ISUP][ISUP] 4        | N/A                   |
| 5                           | [ISUP][ISUP] 5        | N/A                   |


### List of [Clinical Information](clinical_information/marksheet.csv/) Descriptors 

| Descriptor                  | Meaning               |
|:----------------------------|:----------------------|
| ```patient_id```            | Anonymized patient ID.                                                                                 | 
| ```study_id```              | Anonymized study ID. Multiple study IDs can be assigned to the same patient ID.                        | 
| ```mri_date```              | Anonymized date at the time of the MRI study.                                                          | 
| ```patient_age```           | Patient age at the time of the MRI study.                                                              | 
| ```psa```                   | [Prostate-specific antigen level (PSA)][PSA] (unit: ng/mL), as stated in the radiology report associated with the MRI study. If this value is missing, then it was not reported for the given study.    | 
| ```prostate_volume```       | Prostate volume (unit: mL), as stated in the radiology report associated with the MRI study. In clinical practice, this value is typically approximated using the [conventional prolate ellipsoid model][PI-RADS]. If this value is missing, then it was not reported for the given study.|
| ```psad```                  | [Prostate-specific antigen density (PSAd)][PSA] (unit: ng/mL²), as stated in the radiology report associated with the MRI study. Note, this value may not neccessarily be the same as the PSA divided by the prostate volume, due to approximations and rounding errors during clinical reporting. If this value is missing, then it was not reported for the given study. | 
| ```histopath_type```        | Procedure used to sample lesion tissue specimen for microscopic or histopathologic analysis. Its value can be ```SysBx``` for [systematic biopsies][SysBx], ```MRBx``` for [MR-guided biopsies][MRBx], ```SysBx+MRBx``` for [systematic][SysBx] and [MR-guided biopsies][MRBx], or ```RP``` for [radical prostatectomy][RP]. If its value is missing, then no tissue sampling procedure was performed; indicating a negative MRI study.|
| ```lesion_GS```             | [Gleason score (GS)][GS] assigned to each lesion after histopathologic analysis, where scores for different lesions are separated by ```,``` (commas). If its value is missing, then no tissue sampling procedure was performed; indicating a negative MRI study. If its value is ```N/A``` only for specific lesion(s), then those lesion(s) (as observed in radiology) were not biopsied or graded in histopathology (typically the case for [PI-RADS][PI-RADS] 1-2 lesions). |


### Dataset Characteristics

| Characteristic              | Frequency       |
|:----------------------------|:---------------:|
| Number of sites                | 11              |
| Number of MRI scanners         | 5 S, 2 P        |
| Number of patients             | 1476            |
| Number of cases                | 1500            |
| — Benign or indolent PCa       | 1075            |
| — csPCa (ISUP ≥ 2)             | 425             |
| Median age (years)             | 66 (IQR: 61–70) |
| Median PSA (ng/mL)             | 8.5 (IQR: 6–13) |
| Median prostate volume (mL)    | 57 (IQR: 40–80) |
| Number of positive MRI lesions | 1087            |
| — PI-RADS 3                    | 246 (23%)       |
| — PI-RADS 4                    | 438 (40%)       |
| — PI-RADS 5                    | 403 (37%)       |
| Number of ISUP-based lesions   | 776             |
| — ISUP 1                       | 311 (40%)       |
| — ISUP 2                       | 260 (34%)       |
| — ISUP 3                       | 109 (14%)       |
| — ISUP 4                       | 41 (5%)         |
| — ISUP 5                       | 55 (7%)         |


### Open-Source Contributions
We encourage open-source contributions! For instance, you can contribute expert-derived delineations of the prostate whole-gland and zonal anatomy at the spatial resolution of axial T2-weighted images. If you're interested, feel free to propose PRs for inclusion to this repo. Pending quality control, substantial contributions will be merged in and credited accordingly.


### Reference
If you are using this dataset or some part of it, please cite the following article:

● [A. Saha, J. J. Twilt, J. S. Bosma, B. van Ginneken, D. Yakar, M. Elschot, J. Veltman, J. J. Fütterer, M. de Rooij, H. Huisman, "Artificial Intelligence and Radiologists at Prostate Cancer Detection in MRI: The PI-CAI Challenge (Study Protocol)", DOI: 10.5281/zenodo.6522364](https://zenodo.org/record/6522364#.YnessuhBy2Q)

**BibTeX:**
```
@ARTICLE{PICAI_BIAS,
    author = {Anindo Saha, Jasper J. Twilt, Joeran S. Bosma, Bram van Ginneken, Derya Yakar, Mattijs Elschot, Jeroen Veltman, Jurgen Fütterer, Maarten de Rooij, Henkjan Huisman},
    title  = {{Artificial Intelligence and Radiologists at Prostate Cancer Detection in MRI: The PI-CAI Challenge (Study Protocol)}}, 
    year   = {2022},
    doi    = {10.5281/zenodo.6522364}
}
```

### License
[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)

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
[PSA]: https://www.cancer.gov/types/prostate/psa-fact-sheet
[SysBx]: https://www.cancer.gov/publications/dictionaries/cancer-terms/def/systematic-biopsy
[MRBx]: https://www.cancer.gov/publications/dictionaries/cancer-terms/def/mri-guided-biopsy
[RP]: https://www.cancer.gov/publications/dictionaries/cancer-terms/def/radical-prostatectomy
[GS]: https://www.cancer.gov/publications/dictionaries/cancer-terms/def/gleason-score
