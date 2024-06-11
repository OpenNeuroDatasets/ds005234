# Prerequisites (necessary Python packages)

1. For installation, we recommend the Anaconda distribution. Find the installation guide here: [Anaconda Installation Guide](https://docs.anaconda.com/anaconda/install/).

2. After you have a working version of Python 3, simply install a new virtual environment via this command in the Ubuntu terminal or Anaconda Prompt for Windows OS:

`conda create --name=mne1.4 --channel=conda-forge python=3.10 mne=1.4.1 numpy=1.23.1 spyder pyvista pyvistaqt pingouin rpy2 mne-bids numpy openpyxl autoreject`


Or use the requirements_xxxxxx.txt files located in this directory:
- For Ubuntu OS (version 20 and above), please use requirements_for_ubuntu_2x.txt.
- For Windows OS (version 10 and above), please use requirements_for_windows_1x.txt.

To do this, you can run the following command in the Ubuntu terminal or Anaconda Prompt for Windows OS:
`conda create --name mne1.4 --file <requirements_filename>`

3. Activate the created environment:
`conda activate mne1.4`

4. Start your favorite IDE with this environment. For example, to start Spyder IDE, use this command after activating the environment:
`spyder`

5. To start processing data, go to the directory with the downloaded data and open the Python scripts of interest. (If you are using Spyder IDE, use the "Files" pane located in the upper right corner of the workspace.)

# Directory Structure

## Code directories

The code of project has the following structure:

```
code
├── analysis
│   ├── 0-preprocessing_for_clustering
│   │   ├── ...
│   ├── 1-tfce_clustering
│   │   ├── ...
│   ├── 2-clustering_results_analytics
│   │   ├── ...
│   └── modules
│       ├── clustering.py
│       └── data_ops.py
├── envs
│   ├── envs_for_between_groups_clustering_in_auditory_cortex_with_morphological_sign_flip.json
│   ├── envs_for_interaction_clustering_in_auditory_cortex_with_morphological_sign_flip.json
│   └── envs_for_within_groups_clustering_in_auditory_cortex_with_morphological_sign_flip.json
├── preprocessing
│   ├── 00-maxwell_filtering.py
│   ├── ...
│   └── 10-make_stc.py
├── README
├── requirements_for_ubuntu_2x.txt
└── requirements_for_windows_1x.txt
```

## Output directories

All output files from the scripts are saved in the derivatives directory instead of the code directory.

Clustering Versions (used in python scripts names and directory names):
- `v13`: TFCE clustering based on groups ⨯ conditions difference response
- `v14`: TFCE clustering based on between-conditions difference response
- `v15`: TFCE clustering based on between groups evoked response

Shortnames of stimuli (used in code, filenames and directory names):
- `dv` - periodic vowels
- `rv` - non-periodic vowels
- `mp` - periodic non-vowels
- `mr` - non-periodic non-vowels

The derivatives of project has the following structure:

```
derivatives/preprocessing/
├── fsaverage_labels_of_analytics
│   ├── auditory_cortex_region-lh.label
│   └── auditory_cortex_region-rh.label
└── fsaverage_stcs_after_morph_flip_in_labels_of_analytics
    ├── subjects_info_for_morphological_sign_flipped_data_1000Hz
    │   ├── 0_brain_with_auditory_ROI.png
    │   ├── 0_TD_and_ASD_subjects_info.tsv
    │   ├── K0059_dv_morphologicaly_flipped_fsaverage_1000Hz_evolution.mp4
    │   ├── K0059_dv_SF_brain.png
    │   │   ├── ...
    │   ├── Z446_mr_SF_brain.png
    │   ├── Z446_rv_morphologicaly_flipped_fsaverage_1000Hz_evolution.mp4
    │   ├── Z446_rv_SF_brain.png
    │   └── Z446_SF_for_1000_Hz.png
    └── subjects_stc_for_morphological_sign_flipped_data_1000Hz
        ├── envs.json
        ├── K0059_dv_morphologicaly_flipped_fsaverage_1000Hz-lh.stc
        │   ├── ...
│   ├── ...
        └── Z446_rv_morphologicaly_flipped_fsaverage_1000Hz-rh.stc

        
derivatives/analysis/
├── 20240607_74subj_v13_500Hz_5000_perm_DV-MR_TD_vs_ASD_0-800_msec_tfce_interaction_in_auditory_cortex_morph_flip_with_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── TD_and_ASD_subjects_mean_SF_value_in_bgROI_morphed_to_fsaverage_brain_for_dv_mr.tsv
├── 20240608_74subj_v13_500Hz_5000_perm_MP-MR_TD_vs_ASD_0-800_msec_tfce_interaction_in_auditory_cortex_morph_flip_with_5e-02_clusters_p_thresh
│   ├── calculations_logs.txt
│   │   ├── ...
│   └── F_obs.npy
├── 20240608_74subj_v13_500Hz_5000_perm_RV-MR_TD_vs_ASD_0-800_msec_tfce_interaction_in_auditory_cortex_morph_flip_with_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── TD_and_ASD_subjects_mean_SF_value_in_bgROI_morphed_to_fsaverage_brain_for_rv_mr.tsv
├── 20240608_74subj_v14_500Hz_5000perm_ASD_DV-MR_0-800_msec_tfce_1samp_within_groups_in_auditory_cortex_morph_flip_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── T_obs.npy
├── 20240608_74subj_v14_500Hz_5000perm_ASD_MP-MR_0-800_msec_tfce_1samp_within_groups_in_auditory_cortex_morph_flip_5e-02_clusters_p_thresh
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── T_obs.npy
├── 20240608_74subj_v14_500Hz_5000perm_ASD_RV-MR_0-800_msec_tfce_1samp_within_groups_in_auditory_cortex_morph_flip_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── T_obs.npy
├── 20240608_74subj_v14_500Hz_5000perm_TD_DV-MR_0-800_msec_tfce_1samp_within_groups_in_auditory_cortex_morph_flip_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── T_obs.npy
├── 20240608_74subj_v14_500Hz_5000perm_TD_MP-MR_0-800_msec_tfce_1samp_within_groups_in_auditory_cortex_morph_flip_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── T_obs.npy
├── 20240608_74subj_v14_500Hz_5000perm_TD_RV-MR_0-800_msec_tfce_1samp_within_groups_in_auditory_cortex_morph_flip_5e-02_clusters_p_thresh
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   ├── stc_with_clusters-rh.stc
│   │   ├── ...
│   └── T_obs.npy
├── 20240608_74subj_v15_500Hz_5000_perm_DV_TD_vs_ASD_in_0-800_msec_tfce_between_groups_in_auditory_cortex_morph_flip_with_5e-02_cluster_p_threshold
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   └── stc_with_clusters-rh.stc
├── 20240608_74subj_v15_500Hz_5000_perm_MP_TD_vs_ASD_in_0-800_msec_tfce_between_groups_in_auditory_cortex_morph_flip_with_5e-02_cluster_p_threshold
│   ├── calculations_logs.txt
│   │   ├── ...
│   └── F_obs.npy
├── 20240608_74subj_v15_500Hz_5000_perm_MR_TD_vs_ASD_in_0-800_msec_tfce_between_groups_in_auditory_cortex_morph_flip_with_5e-02_cluster_p_threshold
│   ├── calculations_logs.txt
│   │   ├── ...
│   └── F_obs.npy
├── 20240608_74subj_v15_500Hz_5000_perm_RV_TD_vs_ASD_in_0-800_msec_tfce_between_groups_in_auditory_cortex_morph_flip_with_5e-02_cluster_p_threshold
│   ├── 0_clusters_evolution_5e-02_clusters_p_threshold_lateral_view.mp4
│   │   ├── ...
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-lh.stc
│   ├── stc_with_clusters_evolution_5e-02_clusters_p_threshold-rh.stc
│   ├── stc_with_clusters-lh.stc
│   └── stc_with_clusters-rh.stc
└── word-in-noise
    ├── probability_map.csv
    ├── README
    └── win_task_result_for_30_td_and_26_asd.csv



```

# User guide for code directory usage

The following steps are presented for Ubuntu OS.
Please before every script executing please check bids_boot variable in code of script and update it if it's nessesary.

# Step 1: Preprocessing

1. Navigate to the preprocessing directory:
```
cd code/preprocessing
```

2. Run each of the preprocessing scripts in the specified order. It is recommended to use an IDE like Spyder for executing these scripts interactively:

```
python 00-maxwell_filtering.py
python 01-make_head_pos.py
python 02-run_trans_to_optimal_pos.py
python 03-run_ssp.py
python 04-run_freesurfer.py
python 05-corregistration.py
python 06-make_bem.py
python 07-make_fwd.py
python 08-make_epochs.py
python 08.1-crop_epochs.py
python 09-make_inv.py
python 10-make_stc.py
```

These scripts perform various preprocessing steps, including Maxwell filtering, head position estimation, coregistration, BEM creation, forward solution computation, epoch creation, and source time course (STC) generation.


# Step 2: Analysis

1. Navigate to the analysis directory:
```
cd ../analysis
```

2. Run the script in the 0-preprocessing_for_clustering directory to prepare data specifically for clustering analysis (make morphological sign correlated flip for all STC-files):

```
python make_stc_within_auditory_labels_and_morphological_sign_flip.py
```

This script generates STC data with morphological sign flips within auditory labels, which is necessary for the subsequent clustering analysis. If you do not intend to perform clustering analysis, you can stop after step ```python 10-make_stc.py```.

3. Run the scripts in the 1-tfce_clustering directory for clustering analysis. Ensure you have the appropriate environment file loaded for the specific clustering analysis you are conducting. Use an IDE like Spyder for executing these scripts:
```
# For interaction clustering
python 1-tfce_clustering/clustering_v13_for_interaction_in_auditory_cortex_with_morphologically_sign_flipped_data.py

# For within groups clustering
python 1-tfce_clustering/clustering_v14_within_groups_in_auditory_cortex_with_morphologically_sign_flipped_data.py

# For between groups clustering
python 1-tfce_clustering/clustering_v15_between_groups_in_auditory_cortex_with_morphological_sign_flipped_data.py
```

4. *Optional*: You can use additional DAG (Directed Acyclic Graph) scripts if you want to automatically compute clustering for all types of stimuli. Run the corresponding DAG scripts in the 1-tfce_clustering directory from the command line. This allows you to interactively observe the temporal estimation of the clustering computation. All logs during the computations will be automatically recorded in the ```code/analysis/1-tfce_clustering/dag_logs``` directory:
```
# For interaction clustering
python 1-tfce_clustering/dag_clustering_v13_for_interaction_in_auditory_cortex_with_morphologically_flipped_data.py


# For within groups clustering
python 1-tfce_clustering/dag_clustering_v14_within_groups_in_auditory_cortex_with_morphologically_flipped_data.py

# For between groups clustering
python 1-tfce_clustering/dag_clustering_v15_between_groups_in_auditory_cortex_with_morphologically_flipped_data.py


# For all versions of clustering
python 1-tfce_clustering/dag_of_calculation_clustering_versions_v13-15.py
```

4. Finally, after clustering analysis, move to the 2-clustering_results_analytics directory to perform results analysis using an IDE like Spyder:
```
python 2-clustering_results_analytics/analytics_of_v13_interaction_clustering_most_stat_different_vertices_and_SF_plots.py
python 2-clustering_results_analytics/analytics_of_v14_within_groups_clustering_most_stat_different_vertices_and_SF_plots.py
```

5. Finally, generate plots and movies for publication using the scripts in the 3-plots_and_movies_for_publication directory with an IDE like Spyder:
```
python 3-plots_and_movies_for_publication/TODO_20240501_p_value_interaction_clusters_video.py
python 3-plots_and_movies_for_publication/TODO_20240516_fig3_v3.py
python 3-plots_and_movies_for_publication/TODO_20240521_fig6_v12.py
python 3-plots_and_movies_for_publication/TODO_20240527_fig4_v10.py
python 3-plots_and_movies_for_publication/TODO_20240527_fig6_sup_v4.py
python 3-plots_and_movies_for_publication/TODO_20240527_timevertices_interaction_clusters_video.py
```

# Notes

* Ensure all dependencies are installed as specified in the requirements files.

* The environment files provided in the envs directory contain configurations for different clustering analyses:

- envs_for_between_groups_clustering_in_auditory_cortex_with_morphological_sign_flip.json
- envs_for_interaction_clustering_in_auditory_cortex_with_morphological_sign_flip.json
- envs_for_within_groups_clustering_in_auditory_cortex_with_morphological_sign_flip.json

These files contain parameters for clustering methods, thresholds, and paths to various data directories. Make sure these paths are correctly set up in your working environment. For all clustering steps (the python-files from code/analysis), use the environment files with descriptive names and update them if any changes to the configuration are needed.

