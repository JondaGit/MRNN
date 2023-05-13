# How to run

Easiest approach is to use MiniConda to create a new Python environment (due to this repository using older versions of Python and Tensorflow) - https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html#regular-installation (MiniConda is sufficient).  
After installing, use the following commands to create a new conda environment (execute in the root folder of this repo):  
`conda create -n tf15 python tensorflow=1.15 scikit-learn`
`conda activate tf15`
At this point you should have conda environment activated. To run the MRNN training and imputation, tun the following command:
`python3 main_mrnn.py --file_name data/cleaned_csv_file.csv --seq_len 7 --missing_rate 0.2 --h_dim 10 --batch_size 128 --iteration 2000 --learning_rate 0.01 --metric_name rmse`

_Original part of the README from the authors_

# Codebase for "Estimating Missing Data in Temporal Data Streams Using Multi-Directional Recurrent Neural Networkss (MRNN)"

Authors: Jinsung Yoon, William R. Zame, Mihaela van der Schaar

Paper: Jinsung Yoon, William R. Zame, Mihaela van der Schaar,
"Estimating Missing Data in Temporal Data Streams Using
Multi-Directional Recurrent Neural Networks,"
IEEE Transactions on Biomedical Engineering, 2019.

Paper Link: https://ieeexplore.ieee.org/document/8485748

Contact: jsyoon0823@gmail.com

This directory contains implementations of MRNN framework for imputation
in time-series data using GOOGLE stocks dataset.

To run the pipeline for training and evaluation on MRNN framwork, simply run
python3 -m main_mrnn.py.

### Command inputs:

- file_name: data file name
- seq_len: sequence length of time-series data
- miss_rate: probability of missing components (to be introduced)
- h_dim: hidden state dimensions
- batch_size: the number of samples in mini batch
- iteration: the number of iteration
- learning_rate: learning rate of model training
- metric_name: imputation performance metric

### Example command

```shell
$ python3 main_mrnn.py --file_name data/google.csv --seq_len 7
--missing_rate: 0.2 --h_dim 10 --batch_size 128 --iteration 2000
--learning_rate 0.01 --metric_name rmse
```

### Outputs

- x: original data with missing
- ori_x: original data without missing
- m: mask matrix
- t: time matrix
- imputed_x: imputed data
- performance: imputation performance
