# Stimulation mapping and whole-brain modeling reveal gradients of excitability and recurrence in cortical networks

This repository includes the code required to reproduce the results in: "Stimulation mapping and whole-brain modeling reveal gradients of excitability and recurrence in cortical networks"

### Journal Information:
Nature Communications (2025)  
DOI: https://doi.org/10.1038/s41467-025-58187-6

### Authors:
- Davide Momi<sub>1,2,13</sub>
- Zheng Wang<sub>1,13</sub>
- Sara Parmigiani<sub>2,3,4</sub>
- Ezequiel Mikulan<sub>5</sub>
- Sorenza P. Bastiaens<sub>1,6</sub>
- Mohammad P. Oveisi<sub>1,7</sub>
- Kevin Kadak<sub>1,6</sub>
- Gianluca Gaglioti<sub>8</sub>
- Allison C. Waters<sub>9</sub>
- Sean Hill<sub>1,6,10</sub>
- Andrea Pigorini<sub>11,12</sub>
- Corey J. Keller<sub>2,3,4,14</sub>
- John D. Griffiths<sub>1,6,7,10,14</sub>

### Affiliations:
<sub>1</sub> Krembil Centre for Neuroinformatics, Centre for Addiction and Mental Health (CAMH), Toronto, Canada  
<sub>2</sub> Department of Psychiatry and Behavioral Sciences, Stanford University Medical Center, Stanford, CA, USA  
<sub>3</sub> Veterans Affairs Palo Alto Healthcare System, Palo Alto, CA, USA  
<sub>4</sub> Wu Tsai Neurosciences Institute, Stanford University, Stanford, CA, USA  
<sub>5</sub> Department of Health Sciences, Università degli studi di Milano, Milan, Italy  
<sub>6</sub> Institute of Medical Science, University of Toronto, Toronto, Canada  
<sub>7</sub> Institute of Biomedical Engineering, University of Toronto, Toronto, Canada  
<sub>8</sub> Department of Biomedical and Clinical Sciences "L.Sacco", Università degli Studi di Milano, Milan, Italy  
<sub>9</sub> Nash Family Center for Advanced Circuit Therapeutics, Icahn School of Medicine at Mount Sinai, New York, NY, USA  
<sub>10</sub> Department of Psychiatry, University of Toronto, Toronto, Canada  
<sub>11</sub> Department of Biomedical, Surgical and Dental Sciences, Università degli Studi di Milano, Milan, Italy  
<sub>12</sub> UOC Maxillo-facial Surgery and dentistry, Fondazione IRCCS Cà Granda, Ospedale Maggiore Policlinico, Milan, Italy  
<sub>13</sub> These authors contributed equally: Davide Momi, Zheng Wang  
<sub>14</sub> These authors jointly supervised this work: Corey J. Keller, John D. Griffiths


#### Please read our paper, and if you use this code, please cite our paper:
Nature Communications (2025) - DOI: https://doi.org/10.1038/s41467-025-58187-6

## Studying RSN input processing strategies and the role of recurrent feedback with computational brain network models.
Shown here is a schematic overview of the hypotheses, methodology, and general conceptual framework of the present work. (A) Intracerebral electrical stimulation (iES) applied to an intracortical target region generates an early (~20-30ms) response (evoked potential waveform component) at high-density scalp electroencephalography (hd-EEG) channels sensitive to that region and its immediate neighbors (red arrows). This also appears in more distal connected regions after a short delay due to axonal conduction and polysynaptic transmission. Subsequent second (~60-80ms) and third (~140-200ms) late evoked components are frequently observed (blue arrows). After identifying the stimulated network in this way, we aim to determine the extent to which this second component relies on intrinsic network activity versus recurrent whole-brain feedback. (B) Schematic of the hierarchical spatial layout of canonical resting-state networks (RSNs) as demonstrated in Margulies et al. (2016), spanning unimodal regions showing greater functional segregation to high-order transmodal regions showing greater functional integration (Mesulam, 1998). (C) Schematic of virtual dissection methodology and key hypotheses tested. We first fit personalized connectome-based computational models of iES-evoked responses to the hd-EEG time series, for each patient and stimulation location. Then, precisely timed communication interruptions (virtual dissections) were introduced to the fitted models, and the resulting changes in the iES-evoked propagation pattern were evaluated. We hypothesized that lesioning would lead to activity suppression in high-order but not low-order networks, demonstrating differential dependence on recurrent feedback across the cortical hierarchy.


![alt text](https://github.com/Davi1990/Momi_et_al_2024/blob/main/img/Figure_1.png)


## Methodological workflow for characterizing the stimulated network and performing subject-specific connectome-based neurophysiological modeling of evoked potentials.

 (A) Simultaneous stereotactic electroencephalography (sEEG) and scalp high-density electroencephalography (hd-EEG) signals were recorded. The black triangle and dashed vertical line indicate the time at which iES was delivered. For further details on the methodology and data preprocessing please refer to Parmigiani et al., 2021 (B) To pinpoint the brain network where the stimulus was delivered, we employed the Schaefer atlas (Schaefer et al., 2018), which divides the brain into 1000 regions across seven distinct RSNs: visual, somatosensory, limbic, dorsal attention, ventral attention, fronto-parietal and default mode. Subsequently, we identified the parcellation region that overlapped with the intracerebral electrode responsible for delivering the stimulus, ultimately enabling us to determine the stimulated network. (C) To model-individual stimulus-evoked time series, the Jansen-Rit model (Jansen and Rit, 1995), a neural mass model comprising pyramidal, excitatory interneuron, and inhibitory interneuron populations, was embedded in every parcel of the lower-resolution 200-region Schaefer atlas (Schaefer et al., 2018) for simulating and fitting neural activity time series. The connectivity between regions was modeled using diffusion-weighted MRI tractography computed from a sample of healthy young individuals from the Human Connectome Project (HCP) Dataset (Van Essen et al., 2012), and then averaged to give a grand-mean anatomical connectome. The iES-induced depolarization of the resting membrane potential was modeled by a perturbing voltage offset to the mean membrane potential of the excitatory interneuron population. Next, a lead field matrix was employed to project the time series from the cortical surface parcels into EEG channel space, resulting in the generation of simulated scalp hd-EEG measurements. The quality of fit (loss) was quantified by calculating the cosine similarity between the simulated and empirical stimulus-evoked time series. Optimization of model parameters was accomplished by leveraging the autodiff-computed gradient (Rall, 1981) between the objective function and the model parameters, employing the ADAM algorithm (Kingma and Ba, 2017). Ultimately, the optimized model parameters were utilized to generate the fitted, simulated (optimized) stimulus-evoked hd-EEG activity.


![alt text](https://github.com/Davi1990/Momi_et_al_2024/blob/main/img/Figure_2.png)


## Data   

The data used in this study were taken from an open dataset collected at the "Claudio Munari'' Epilepsy Surgery Center of Milan in Italy (https://doi.org/10.17605/OSF.IO/WSGZP), where simultaneous stereotactic electroencephalography (sEEG) and high-density scalp EEG (hd-EEG) was recorded following intracortical single pulse electrical stimulation on 36 patients (median age = 33 ± 8 years, 21 female). All subjects had a history of drug-resistant, focal epilepsy, and were candidates for surgical removal/ablation of the seizure onset zone (SOZ). For details regarding the data acquisition and the preprocessing steps please refer to the original papers (Mikulan et al., 2020, Parmigiani et al., 2022).
In addition, it includes the spatial locations of the stimulating contacts in native MRI space, MNI152 space and Freesurfer's surface space, as well as the digitized positions of the 185 scalp hd-EEG electrodes. It also contains the MRI of each subject, de-identified with AnonyMi (Mikulan et al., 2021). Structural MRI data used in this study for specifying anatomical connectivity priors are available from the original Human Connectome Project dataset (Van Essen et al., 2012), and have been used for similar purposes in previous work (Momi et al. 2023) .



## Notebooks
This repository contains Jupyter notebooks that replicate the code and results presented in our paper. Each notebook serves a specific purpose as described below:

| Notebook | Run | View | Description |
| - | --- | ---- | ----------- |
| Calculate_distances | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/code/Calculate_distances.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/Momi_et_al_2024/blob/main/code/Calculate_distances.ipynb?flush_cache=true) | This notebook demonstrates how to calculate the distances for determining which network was stimulated. |
| Plot_channel_location | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/code/Plot_channel_location.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/Momi_et_al_2024/blob/main/code/Plot_channel_location.ipynb?flush_cache=true) | This notebook plots each subject's sEEG on an MNI template. |
| Replicating Empirical Results | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/code/Empirical.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/Momi_et_al_2024/blob/main/code/Empirical.ipynb?flush_cache=true) | This notebook replicates the empirical results for sEEG and hd-EEG. |
| Model_fitting | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/code/Model_fitting.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/Momi_et_al_2024/blob/main/code/Model_fitting.ipynb?flush_cache=true) | This notebook shows how to estimate model parameters and run the model using the fitted parameters. |
| Replicating Virtual dissection Results | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/code/Virtual_dissection.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/Momi_et_al_2024/blob/main/code/Virtual_dissection.ipynb?flush_cache=true) | This notebook replicates the modeling results using the virtual dissections approach. |
| Replicating Applying virtual dissection | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Davi1990/Momi_et_al_2024/blob/main/code/Applying_virtual_dissection.ipynb) | [![View the notebook](https://img.shields.io/badge/render-nbviewer-orange.svg)](https://nbviewer.jupyter.org/github/Davi1990/Momi_et_al_2024/blob/main/code/Applying_virtual_dissection.ipynb?flush_cache=true) | This notebook shows how the virtual dissection was applied. |


## References
- Jansen BHRit VG (1995) Electroencephalogram and visual evoked potential generation in a mathematical model of coupled cortical columns Biological Cybernetics 73:357–366. https://doi.org/10.1007/BF00199471
- Kingma DPBa J (2017) Adam: A Method for Stochastic Optimization arXiv. https://arxiv.org/abs/1412.69
- Mikulan, E., Russo, S., Parmigiani, S., Sarasso, S., Zauli, F. M., Rubino, A., Avanzini, P., Cattani, A., Sorrentino, A., Gibbs, S., Cardinale, F., Sartori, I., Nobili, L., Massimini, M., & Pigorini, A. (2020). Simultaneous human intracerebral stimulation and HD-EEG, ground-truth for source localization methods. Scientific Data, 7(1), Article 1. https://doi.org/10.1038/s41597-020-0467-x
- Momi, D., Zheng, W., Griffiths, D.J. (2023). TMS-evoked responses are driven by recurrent large-scale network dynamics. eLife 12:e83232. https://doi.org/10.7554/eLife.83232
- Parmigiani, S., Mikulan, E., Russo, S., Sarasso, S., Zauli, F. M., Rubino, A., Cattani, A., Fecchio, M., Giampiccolo, D., Lanzone, J., D'Orio, P., Del Vecchio, M., Avanzini, P., Nobili, L., Sartori, I., Massimini, M., & Pigorini, A. (2022). Simultaneous stereo-EEG and high-density scalp EEG recordings to study the effects of intracerebral stimulation parameters. Brain Stimulation, 15(3), 664–675. https://doi.org/10.1016/j.brs.2022.04.007
- Rall LB (1981) Automatic Differentiation: Techniques and Applications Springer. https://doi.org/10.1007/3-540-10861-0
- Schaefer AKong RGordon EMLaumann TOZuo XNHolmes AJEickhoff SBYeo BTT (2018) Local-global parcellation of the human cerebral cortex from intrinsic functional connectivity MRI Cerebral Cortex 28:3095–3114. https://doi.org/10.1093/cercor/bhx179
- Van Essen DCUgurbil KAuerbach EBarch DBehrens TEJBucholz RChang AChen LCorbetta MCurtiss SWDella Penna SFeinberg DGlasser MFHarel NHeath ACLarson-Prior LMarcus DMichalareas GMoeller SOostenveld RPetersen SEPrior FSchlaggar BLSmith SMSnyder AZXu JYacoub EConsortium W-MH (2012) The human connectome project: a data acquisition perspective NeuroImage 62:2222–2231. https://doi.org/10.1016/j.neuroimage.2012.02.018