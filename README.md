# Song Title Generation (NLP Summarization Task)

### Introduction

In this tutorial we will be fine tuning a transformer model for **Summarization Task**. 
In this task a song title of a given lyric is generated when passed through a network. The network creates new sentences to encapsulate maximum gist of the text and generates that as output. The sentences in the summary may or may not be contained in the text. 

In this tutorial we will be generating this ***Abstractive Summary***. 

### Flow of the notebook

The notebook will be divided into separate sections to provide a organized walk through for the process used. This process can be modified for individual use cases. The sections are:

1. [Preparing Environment and Importing Libraries](#section01)
2. [Preparing the Dataset for data processing: Class](#section02)
3. [Fine Tuning the Model: Function](#section03)
4. [Validating the Model Performance: Function](#section04)
5. [Main Function](#section05)
    * [Initializing WandB](#section501)
    * [Importing and Pre-Processing the domain data](#section502)
    * [Creation of Dataset and Dataloader](#section503)
    * [Neural Network and Optimizer](#section504)
    * [Training Model and Logging to WandB](#section505)
    * [Validation and generation of Summary](#section506)
6. [Examples of the Summary Generated from the model](#section06)


### Technical Details

This script leverages on multiple tools designed by other teams. Details of the tools used below. Please ensure that these elements are present in your setup to successfully implement this script.

- **Data**:
	- We are using the Song lyrics from 79 musical genres dataset available at [Kaggle](https://www.kaggle.com/datasets/neisse/scrapped-lyrics-from-6-genres?select=lyrics-data.csv)
	- All the data were obtained by scraping the Brazilian website Vagalume using R by the ower of the data set on kaggle. We are referring only to the second csv file from the data dump: `lyrics-data.csv`
	- After preprocessing, there are`191814` rows of data.  Where each row has the following data-point:
		- **title** : Song's name
		- **ctext** : Song lyrics
		- **Number_of_words**: Number of words in lyrics
		- **Number_of_words_title**: Number of words in title


- **Language Model Used**: 
    - This notebook uses one of the most recent and novel transformers model ***T5***. [Research Paper](https://arxiv.org/abs/1910.10683)    
    - ***T5*** in many ways is one of its kind transformers architecture that not only gives state of the art results in many NLP tasks, but also has a very radical approach to NLP tasks.
    - **Text-2-Text** - According to the graphic taken from the T5 paper. All NLP tasks are converted to a **text-to-text** problem. Tasks such as translation, classification, summarization and question answering, all of them are treated as a text-to-text conversion problem, rather than seen as separate unique problem statements.
    - **Unified approach for NLP Deep Learning** - Since the task is reflected purely in the text input and output, you can use the same model, objective, training procedure, and decoding process to ANY task. Above framework can be used for any task - show Q&A, summarization, etc. 
   - We will be taking inputs from the T5 paper to prepare our dataset prior to fine tuning and training.    
   - [Documentation for python](https://huggingface.co/transformers/model_doc/t5.html)

![**Each NLP problem as a “text-to-text” problem** - input: text, output: text](https://miro.medium.com/max/4006/1*D0J1gNQf8vrrUpKeyD8wPA.png) 
	 


- Hardware Requirements: 
	- Python 3.6 and above
	- Pytorch, Transformers and
	- All the stock Python ML Library
	- GPU enabled setup 
   

- **Script Objective**:
    - The objective of this script is to fine tune ***T5 *** to be able to generate title (summary task), that a close to or better than the actual title while ensuring the important information from the lyrics is not lost.
    - Model version 3 training loss example:


![alt test](https://raw.githubusercontent.com/victorlifan/song_title_generation_-NLP-Summarization-Task-/main/img/V3_trainloss.png)

### Notebooks:
1. Detailed Walkthrough: `transformers_summarization_wandb.ipynb`
2. Final model generation: `song_title_generation.ipynb`

### Scripts:
Versions of complete model training processes with different parameters based on `transformers_summarization_wandb.ipynb`

### Logs:
Training logs based on different versions of training scripts.

### Results:
Title generation results based on different versions of training scripts.
