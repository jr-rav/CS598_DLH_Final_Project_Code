# CS598_DLH_Final_Project_Code
Code for Final Project for CS598 UIUC

This repository contains replication of the experiments performed in the paper below for UIUC CS598 Deep Learning For Helthcare Final Project by Jaimin Raval and Mohammed Awan, 
the code was re-used for pre-processing and training the models. 

_Benchmarking Deep Learning Architectures for predicting Readmission to the ICU and Describing patients-at-Risk_

by _Sebastiano Barbieri, James Kemp, Oscar Perez-Concha, Sradha Kotwal, Martin Gallagher, Angus Ritchie, Louisa Jorm_

_Nature Scientific Reports_

https://www.nature.com/articles/s41598-020-58053-z

original citation:

Barbieri, S., Kemp, J., Perez-Concha, O. et al. Benchmarking Deep Learning Architectures for Predicting Readmission to the ICU and Describing Patients-at-Risk. Sci Rep 10, 1111 (2020). https://doi.org/10.1038/s41598-020-58053-z

Here is the code for the original repo: https://github.com/sebbarb/time_aware_attention

The MIMICIII dataset was used that can be downloaded via PhysioNet

The code developed by us contains the following directories and important files:

data  - This directory contains the csv files and the pickle files for all the pre-processed data that was generated during the pre-processing operations of the code. These files are used to 
        get a final dataset used by the training and testing modules of the code. 
        
related_code/data_load.py  -- Contains the code to load the initial data from the MIMICIII dataset. 

 
related_code/hyperparameters.py -- Contains constants that are hyperparameters such as epochs, dropout, train and testing data length, constants to state where the MIMICIII dataset is based, and a constant specifying where to dump the 
pre-processed data and lastly the model.


related_code/modules.py -- contains all the non ODE embedding model architecture.
 

related_code/modules_ode.py  -- contains models that use ODE embeddings
 

related_code/preprocessing_CHARTS_PRESCRIPTIONS.py -- preprocesses CHARTS Prescriptions data from the  MIMICIII dataset and converts it to csv and pickle files.


related_code/preprocessing_create_arrays.py -- this code file when run creates tensor arrays wuth the combined dataset


related_code/preprocessing_DIAGNOSES_PROCEDURES.py -- preprocesses DIAGNOSES_PROCEDURES data from the  MIMICIII datasetand converts it to csv and pickle files.


related_code/preprocessing_ICU_PAT_ADMIT.py -- preprocesses ICU_PAT ICU patient information data from the  MIMICIII datasetand converts it to csv and pickle files.


related_code/preprocessing_merge_charts_outputs.py  -- merges all the reduced charts into one chart using pandas.


related_code/preprocessing_reduce_charts.py -- reduces the chart prescriptions and ICU Patient admission data to only include important data points


related_code/preprocessing_reduce_outputs.py -- reduces the combined output vector to include the important components only.


test.py -- code that tests the data


train.py -- code that loads and trains the appropriate model. 


Training.ipynb -- Notebook that was used in Google Collab Pro to mount the code from google drive with pre-processing done locally and running the train.py by uncommenting
the appropriate model and tuning the hyperparameters in hyperparameters.py accordingly. This will train the model in Google Collab Pro using a Nvidia Tesla GPU


Testing.ipynb -- Notebook that was used in Google Collab Pro to mount the code from google drive with pre-processing done locally and running the test.py by uncommenting
the appropriate model and tuning the hyperparameters in hyperparameters.py accordingly. This will test the model in Google Collab Pro using a Nvidia Tesla GPU

Table of Results.docx -- a table with the original results and our results for 6 replicated models. 

There are no pretrained models available for this project. 

Dependencies: The paper requires pytorch version 1.1, torchdiffeq library 0.2.2 for ODE embeddings, numpy 1.19, pandas 1.2.3

Steps to reproduce data:

The steps for reproducibility would be be to follow the following steps to perform pre-processing:
1.	Run the proprocessing_*.py scripts one at a time to generate the csv files and the pickle files required for the training data. This include running the following files in order:
●	data_load.py – loads the data
●	preprocessing_ICU_PAT_ADMIT.py – loads and extracts patient admission data
●	preprocessing_DIAGNOSES_PROCEDURES.py – Loads an and preprocesses procedures form the MIMIC III data
●	preprocessing_CHARTS_PRESCRIPTION – Loads and pre-process prescription medication from MIMIC III dataset
●	preprocessing_merge_chart_outputs.py – merges the datasets generated above with the appropriate features
●	preprocessing_reduce_charts.py – reduces the data extracted from the various charts 
●	preprocessing_create_arrays.py – creates final arrays of features that can be used by the training model
2.	Adjust the hyperparameters.py and select the appropriate parameters and models
3.	Run the train.py. This can be run in Google Collab Pro by exporting the code after preprocessing into Google Drive and running the train.py in the notebook cell
4.	Run the test.py that gives the statistical information like precision, sensitivity, specificity, F1 Score and AUROC.





