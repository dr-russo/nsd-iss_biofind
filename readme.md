# Code and Analysis 

## New Diagnostic and Staging Framework Applied to Established PD in the BioFIND Cohort

Applies Neuronal $\alpha$-Synuclein Disease Integrated Staging System (NSD-ISS) to the BioFIND cohort with relatively advanced Parkinson's disease.

Marco J. Russo*, MD, PhD, Un Jung Kang, MD for the BioFIND Study  
*Correspondence: MJR: marco.russo@rutgers.edu

**Abstract**  
The newly proposed research framework for diagnosis and staging of Parkinson’s disease (PD) – Neuronal α-Synuclein Disease Integrated Staging System (NSD-ISS) – which anchors PD diagnosis and staging to antemortem α-synuclein detection and existing clinical measures, was recently applied to established cohorts of early PD.  Here, we provide a complementary analysis of more advanced PD by applying NSD-ISS to the BioFIND study cohort. Within BioFIND, 104 participants (96%) were α-synuclein seed amplification assay positive (S+). BioFIND S+ participants were heavily concentrated within ISS stages 3 and 4 (~90%). Disease durations within each ISS stage were highly variable, with significant overlap across stages. Cognitive and non-motor anchors had little weight in determining staging in this cohort. Analysis of NSD-ISS applied to a more advanced PD cohort, we highlight important strengths and limitations of the new framework.

**NOTEBOOKS**
* **biofind_ledd.ipynb**  
Cleans concomitant medication log for BioFIND and calculate the levodopa-equivalent dailiy doses (LEDD) => biofind_ledd.csv
* **nsd-iss_biofind_tidying.ipynb**   
tidy and consolidate all BioFIND clinical data and $\alpha$-Syn-SAA data to faciliate application of NSD-ISS  
* **nsd-iss_biofind_analysis.ipynb**  
ISS staging and analysis of BioFIND participants

**LIBRARIES**
* pandas  
* numpy
* thefuzz
* matplotlib
* seaborn
* scikit-learn (linear regression)  

**BioFIND DATA FILES**  
Data  obtained from the Fox Investigation for New Discovery of Biomarkers  (BioFIND) database, which is part of the USC Laboratory of Neuro Imaging (LONI) Image & Data Archive (IDA), through limited Data Use Agreement: https://ida.loni.usc.edu/collaboration/access/appLicense.jsp. For up-to-date information on the study, visit [www.michaeljfox.org/biofind](www.michaeljfox.org/biofind).

The following BioFIND data files were downloaded and utilized for this analysis.  Note, upon download, .csv file names have date of download appended as _%d%b%Y format, so adjust filenames accordingly:
* Primary_Diagnosis_23Mar2024.csv 
* Screening_Demographics_23Mar2024.csv 
* MDS_UPDRS_Part_I__Patient_Questionnaire_23Mar2024.csv
* MDS_UPDRS_Part_I_23Mar2024.csv
* MDS_UPDRS_Part_II__Patient_Questionnaire_23Mar2024.csv
* MDS_UPDRS_Part_III__Post_Dose__23Mar2024.csv
* MDS_UPDRS_Part_IV_23Mar2024.csv 
* Use_of_PD_Medication_23Mar2024.csv
* REM_Sleep_Disorder_Questionnaire_23Mar2024.csv
* Montreal_Cognitive_Assessment__MoCA__23Mar2024.csv
* Biospecimen_Analysis_Results_23Mar2024.csv
* PD_Features_23Mar2024.csv
* Concomitant_Medication_Log_23Mar2024.csv => biofind_ledd.csv

**DERIVED DATA FILES**  
* biofind_ledd.csv  : *created by biofind_ledd.ipynb; calculated LEDD for BioFIND participants* 

**OUTPUTS**
* biofind_mds-updrs_data.csv : *consolidated data table for all MDS-UPDRS data*

**ABBREVIATIONS**  
PD: Parkinson's disease  
BioFIND: Fox Investigation for New Discovery of Biomarkers (BioFIND) cohort study  
LEDD: levdopa-equivalent daily dose  
MDS-UPDRS: Movement Disorder Society Unified Parkinson’s Disease Rating Scale  
MoCA: Montreal Cognitive Assessment  
NSD: Neuronal Synuclein Disease  
ISS: Integrated Staging System  
RBD: REM sleep behavior disorder  


#### Staging Anchors for NSD-ISS

<ref>Dam, T. et al. Neuronal alpha-Synuclein Disease integrated staging system performance in PPMI, PASADENA, and SPARK baseline cohorts. npj Parkinsons Disease 10, 178 (2024).</ref>

|  	|  	| 	|  	|  	| Anchors of clinical signs or symptoms (stages 2A and 2B) and functional impairment (stages 3-6)<sup>1, 2</sup> 	|
|---	|:---:	|:---:	|:---:	|---	|---	|
|   Stage   	|   S   	|   D<sup>a</sup>   	|   G   	|   Domain   	|   Anchor(s)   	|
|   Stage 0   	|   -   	|   -   	|   SNCA<sup>b</sup>   	|   —   	|   —   	|
|   Stage 1A   	|   +   	|   -   	|   ±   	|   (1) Cognitive <br>   (2) Motor <br>   (3) Other non-motor   	|   (1) MDS-UPDRS item 1.1 = 0; and <br>   (2a) Does not have subthreshold parkinsonism<sup>c</sup>; **and** (2b) is not on PD meds; and  <br> (3a) Does not have RBD; and (3b) is not hyposmic<sup>d</sup>   	|
|   Stage 1B   	|   +   	|   +   	|   ±   	|  	|  	|
|   Stage 2A   	|   +   	|   -   	|   ±   	|   (1) Cognitive<br>    (2) Motor<br>    (3) Other non-motor<br>   	|   (1) Item 1.1 = 1 AND MoCA ≥ 25; or<br>    (2a) Has subthreshold parkinsonism<sup>c</sup>; or (2b) is on PD meds; or<br>    (3a) Has RBD; or (3b) is hyposmic<sup>d</sup>   	|
|   Stage 2B   	|   +   	|   +   	|   ±   	|  	|  	|
|   Stage 3   	|   +   	|   +   	|   ±   	|   (1) Cognitive<br>    (2) Motor<br>   	|   (1a) Item 1.1 = 1 AND MoCA ≤ 24; or (1b) Item 1.1 = 2 AND MoCA ≥ 25; or <br>    (2) MDS-UPDRS-II = 3-13 AND either subthreshold parkinsonism<sup>c</sup> or PD meds   	|
|   Stage 4   	|   +   	|   +   	|   ±   	|   (1) Cognitive<br>    (2) Motor<br>    (3) Other non-motor   	|   (1a) Item 1.1 = 2 and MoCA ≤ 24; or (1b) item 1.1 = 3 AND MoCA ≥ 25; or<br>    (2) MDS-UPDRS-II = 14-26; or<br>    (3) MDS-UPDRS-I (excluding item 1.1) = 13-24<sup>e</sup>   	|
|   Stage 5   	|   +   	|   +   	|   ±   	|   (1) Cognitive<br>   (2) Motor<br>    (3) Other non-motor   	|   (1a) Item 1.1 = 3 AND MoCA ≤ 24; or (1b) item 1.1 = 4 AND MoCA ≥ 25; or<br>    (2) MDS-UPDRS-II = 27-39; or<br>    (3) MDS-UPDRS-I (excluding item 1.1) = 25-36   	|
|   Stage 6   	|   +   	|   +   	|   ±   	|   (1) Cognitive<br>    (2) Motor<br>    (3) Other non-motor   	|   (1) Item 1.1 = 4 AND MoCA ≤ 24; or<br>    (2) MDS-UPDRS-II ≥ 40; or<br>    (3) MDS-UPDRS-I (excluding item 1.1) ≥ 37   	|

*1* Presence of qualifying signs/ symptoms in any single domain qualifies for stage 2 but individuals can have combination in all 3 domains.<br>
*2* Presence of qualifying functional impairment in any single domain qualifies for stage 3-6 but individuals can have combination in all 3 domains.<br>
*a* D positivity defined as < 75% age/sex-expected lowest putamen SBR.<br>
*b* Only fully penetrant pathogenic SNCA variants qualify for Stage 0.<br>
*c* Subthreshold parkinsonism defined as **MDS-UPDRS-III ≥ 5** excluding postural and action tremor.<br>
*d* Hyposmia defined as UPSIT percentile ≤ 15 (age and sex adjusted).<br>
*e* MDS-UPDRS-I (excluding item 1.1) ≥ 13 is sufficient for stage 4 provided that stage 2 criteria are met.<br>
<sub>MDS-UPDRS=Movement Disorder Society Unified Parkinson’s Disease Rating Scale. MoCA=Montreal Cognitive Assessment. NSD=Neuronal Synuclein Disease. PD=Parkinson’s disease. RBD=REM sleep &behavior disorder. UPSIT= University of Pennsylvania Smell Identification Test</sub>
