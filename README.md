<br/>
<h1 align="center">Predator</h1>
<h2 align="center">Predicting the Impact of Cancer Somatic Mutations on Protein-Protein Interactions</h2>
<br/>

[Predator](https://github.com/abu-compbio/Predator/) is a computational tool that offers both 
the prediction of mutation effects on protein-protein interactions by classifying them 
into disrupting and nondisrupting and provides a comprehensive analysis on candidate cancer 
associated genes, their most frequently disrupted interaction partners, cancer patients and 
several cancer cohorts in TCGA project.

For more information, please refer to the article which can be found at [here](https://www.google.com).

<br/>
<p align="center">
    <img width="100%" src="https://raw.githubusercontent.com/ibrahimberb/Predator/main/src/figures/main_steps_2022-03-29.svg" alt="ProtTrans Attention Visualization">
</p>
<br/>

## Reproducibility
Below are the steps to obtain the results in the paper.

### Preparing the _Predator_ environment
1. Download the repository and move to the _reproducible_ folder.\
``cd \Predator\src\reproducible``


2. Update the conda base\
``conda update conda -n base -y``


3. _conda-forge_ needs to be added for installations of packages.
``conda config --append channels conda-forge``


4. Create a new environment named _predator_ with a specified Python version and install required packages.\
``conda create python=3.8.13 --name predator --file requirements.txt -y``


5. Activate new environment.\
``conda activate predator``


6. Adding _ipykernel_ to this new environment named _Predator_.
``python -m ipykernel install --user --name predator --display-name "Predator"``


### Training the _Predator_
The trained model can be found in [here](https://github.com/abu-compbio/Predator/tree/main/src/PredatorModels/PredatorModel_2022-06-16/cc84a54e). In order to train from scratch, 
please execute the following command:

``python reproducable_01_training_predator.py``

Newly trained model will be extracted in 
_src\PredatorModels\PredatorModel\_<date\>\\\<hash>_ directory. Additionally, a new executed
Jupyter notebook _Reproduced_PredatorStudyModel.ipynb_ will be created in _reproducible_ folder.

### Predictions on the TCGA Mutation Datasets

Trained Predator model can be applied to TCG mutation datasets with 
_reproducable_01_training_predator.py_. The script also allows the selection of 
the model to be used in the prediction task. Simply run the following command to execute:

``python reproducable_02_predicting_tcga.py``

This will export prediction files in _predictions_datasets_ folder and 
create _Reproduced\_PredatorStudy\_<TCGA\>\.ipynb_ for each TCGA cohort.

### Patient Interaction Analysis

If the path of prediction files are not to be updated, the patient interaction analysis 
files are generated by the following command:

``python reproducable_03_patient_interaction_analysis.py``

The paths of newer prediction datasets can be updated in the script before running it.
Upon completion, Excel files containing interactions and patients for each TCGA should
appear in _data/patient_interaction_datasets_ folder. Also, _Reproduced_Disruptive_patients_per_patient.ipynb_
will be created in executed form.

### Analysis

Lastly, update the path if necessary in _reproducible_04_analysis.py_ and run it
with the command below:

``python reproducible_04_analysis.py``

Execution of this command will create counts file for each TCGA.

Run the first part of the notebook _tables/preliminary_tables_counts.ipynb_ as indicated.

Run the notebook _analyses/PatientInteractionAnalysis/PatientInteractionAnalysis.ipynb_.

Continue with the second part of the _tables/preliminary_tables_counts.ipynb_, which
the Gene Level Statistics table will be generated.
