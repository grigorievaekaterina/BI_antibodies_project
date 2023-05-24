## Sufficient mutation landscape for machine learning of antibody binding
Authors:

Ekaterina Grigorieva \
Daria Balashova

### Description

This repository was created for the main project in Bioinformatics Institute. Here you can find [the code](https://github.com/grigorievaekaterina/BI_antibodies_project/tree/main/code) and obtained [results](https://github.com/grigorievaekaterina/BI_antibodies_project/tree/main/results).

### Introduction

More and more information has been gathered on mutations in the RBD of the Wu-Hu-1, which is a key site for neutralizing antibodies. Because of this, ML models can be developed to predict how well antibody evasion will occur when faced with a multitude of mutation data.

Nevertheless, certain mutations in the RBD can affect antibody binding in a similar way, allowing ML models to be trained to determine the efficacy of a specific antibody by using data from other antibodies as a reference.

In this study we conducted experiments involving machine learning and deep learning models trained with RBD mutations neutralized by four antibodies: REGN10933, LY-CoV16, LY-CoV555, and REGN10987. The data was used from [Taft et. al., 2022](https://pubmed.ncbi.nlm.nih.gov/36150393/).

### Results

First of all, we represented Random Forest (RF) models from the article.
![Representing results](https://github.com/grigorievaekaterina/BI_antibodies_project/assets/113314957/67b9f62b-861d-491f-9ba0-cf8a7aed0187)

Then we decided to create new RF models. For this task we preprocessed data using one-hot encoding. The figure below shows the meaning of this step (taken from [Guobin Li et. al., 2021](https://pubmed.ncbi.nlm.nih.gov/33986992/)). Also we tagged each sequence in every dataset with the flag according to the antibody (additional array with the number one at zero position for LY16, first for LY555, second for REGN33, third for REGN87)

<img width="275" alt="Снимок экрана 2023-05-25 в 00 13 50" src="https://github.com/grigorievaekaterina/BI_antibodies_project/assets/113314957/c609b2a5-1c11-4509-a5ff-9c297c9a13b1">

Four models were trained and tested on separated data, the structure of each one presented below.

<img width="252" alt="Снимок экрана 2023-05-25 в 00 14 35" src="https://github.com/grigorievaekaterina/BI_antibodies_project/assets/113314957/8a149ab8-d232-4088-9bee-188857550deb">

The fifth model was trained on combined train data from previous four models. After training we seperately tested Model 5 on data from Model 1 to Model 4.

<img width="335" alt="Снимок экрана 2023-05-25 в 00 18 33" src="https://github.com/grigorievaekaterina/BI_antibodies_project/assets/113314957/a7ffcf49-fba4-4d86-adb1-a43e6935e192">

Thus, we wanted to show how additional (different antibodies) data depends on the prediction quality. Results indicated the increase of ROC-AUC score in the case with REGN87, that means training model on different data was useful.

![ROC-AUC only](https://github.com/grigorievaekaterina/BI_antibodies_project/assets/113314957/c4a10871-de50-4de0-a84f-f07bac253a36)

Our group tried other machine learning methods too. The results and code can be found [here](https://github.com/GavrilenkoA/ML_mutational_learning)

### Further plans
* Try to achieve the same metrics as full data configuration using transfer-learning method with limited data.
* Collect dataset of mutations data allowing to get the more accurate predictions.
