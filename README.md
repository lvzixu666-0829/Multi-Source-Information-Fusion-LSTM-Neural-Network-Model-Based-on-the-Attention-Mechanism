# Multi-Source-Information-Fusion-LSTM-Neural-Network-Model-Based-on-the-Attention-Mechanism
The reproducibility package was assembled on March 2, 2026. It was assembled by three authors: huicong Liu​ (responsible for The improved LSTM model, contact: lcong0308@gmail.com), yinghan Zhang​ (responsible for Time series model, contact: zhaoyinghan97@163.com), and zixu Lv​ (responsible for Asset pricing model, contact: lvzixu666@163.com). 


The computing environment: 
Operating System: Windows
Python (Version: 3.8.20), Stata (Version: 17)
language: English, Chinese
Packages: 
	Python==3.8.20
	PyTorch==2.1.2（CUDA 11.8 + cuDNN 8）
	pandas==2.0.3
	openpyxl==3.1.5
	pillow==10.4.0
	numpy==1.24.4
	matplotlib==3.7.2
	scikit-learn==1.3.0
It is recommended to use Anaconda/Miniconda to manage the environment.

The analyses in this paper utilize publicly available data from the following sources: Tokenview, Investing.com, Google Trends, and Baidu Index. All datasets are sourced from publicly accessible channels, ensuring transparency and replicability. The complete data processing pipeline, including all cleaning, transformation, and feature engineering steps, is thoroughly documented and implemented within the corresponding code files provided in our reproducibility kit.

Our reproducibility package is organized into two main directories: Data&Model and Results, ensuring a clear separation of source materials and research outputs. The detailed organization of the reproducibility package is as follows:
Reproducibility_package/
├── Results
│   ├── Tables
│   └── Figures
└── Data&Model
    ├── 1 The improved LSTM model
    │   ├── ablation_experiment/      # Ablation study code
    │   ├── Backtesting system/       # Backtesting module (strategy validation & performance evaluation)
    │   ├── ML/                       # Traditional machine learning models
    │   ├── train/                    # Deep learning training module (training scripts)
    │   ├── test/                     # Testing scripts and independent experiment validation
    │   └── README-improved LSTM model.md                 # Project documentation
    ├── 2 Time series model
    │   ├── code/
    │   ├── rawdata/
    │   └── Readme-time series model.txt
    └── 3 Asset pricing model
        ├── code/
        └── rawdata/ 

The Results directory contains the complete set of research outputs:
• All statistical tables referenced in the main text of the paper
• All supplementary tables and figures included in the appendix
• All visualizations and figures in JPG format, corresponding to those presented in the manuscript

Reproduction Workflow
To regenerate our research results:
	Execute the code files in each model directory using the corresponding software (Python or Stata)
	Process the raw data through the analytical pipelines
	The final outputs will match the tables and figures provided in the Results directory

The Data directory houses the research infrastructure organized by methodological approach:

1 The improved LSTM model
##ablation_experiment/
This directory contains the code and experimental results for the Ablation Study. In this project, four different BTC factor feature sets are constructed, each corresponding to different categories of information sources.
The ablation experiments are conducted as follows:
	Train the model using only one group of factors at a time
	Keep the model architecture and training hyperparameters unchanged
	Compare the predictive performance across different factor groups
	How to Switch Factor Groups
To switch between different factor combinations, modify the following file: model/lstm.py
Specifically, locate:
self.lstm = nn.LSTM(
    input_size=canshu['input_size_1'],
)
Parameters to Modify
input_size_1
input_size_2
input_size_3
input_size_4
These parameters correspond to the feature dimensions of the four BTC factor groups.

##Train/
Deep learning training module, including:
	Improved LSTM model definition
	Main training script
	Custom loss functions
	Learning rate scheduling strategy
	Model checkpoint saving (.ckpt)
This module supports further training and reproduction of experiments based on the original dataset.
Dataset Split Configuration：
In config.py, the Group parameter controls different time-based dataset splits:
	Group1-baseline
	Group2-'17-3-3_17-9-3'
	Group3-'17-9-4_18-3-4'
	Group4-'19-7-29_20-1-29'
	Group5-'20-1-30_20-7-30'
	Group6-'21-8-24_22-2-23'
	Group7-'22-2-24_22-8-24'

##test/
Testing and strategy generation module, including:
	Prediction result validation
	Performance metric calculation
	Confusion matrix visualization
	Trading strategy generation
	Reproducing Main Experimental Results
run python test.py
Then run: python strategy.py
This script will generate trading signals based on the predicted price movement (up/down).

##Backtesting system/
Quantitative backtesting module, mainly used for:
	Evaluating trading strategies generated by the model
	Calculating returns and cumulative return curves
	Computing performance metrics such as:
	Maximum Drawdown
	Sharpe Ratio
	Visualizing strategy performance

##ML/
This module reproduces experimental results using traditional machine learning methods.


2 Time series model and Asset pricing model
##code/: Python scripts implementing the time series model
##rawdata/: Source datasets required for training and evaluating the time series model

3 Asset pricing model
##code/: Stata do-files implementing the asset pricing model
##rawdata/: Source datasets for data processing, integration, and model estimation


It is noticed that, all datasets necessary to replicate the results in this paper are included within the replication kit. As the data is obtained from public platforms, there are no specific access restrictions. However, users should be mindful of the terms of use​ associated with each platform, which typically govern commercial use and redistribution. The raw data, as retrieved, and the processed versions used to generate the paper's results are included in the replication package for straightforward replication.