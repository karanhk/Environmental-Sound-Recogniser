# About

## Abstract

This repository classifies audio recording into 50 sound categories with **70% accuracy** using convolutional neural network (CNN). It creates spectrogram from audio file by `librosa` library and classifies that spectrogram by using CNN.

## Detailed

This is a repository to classify audio recording into 50 sound categories including animal sound, natural sound, human non-speech sound, domestic sound, urban noises and many more. It is trained on [esc50]("https://www.kaggle.com/datasets/mmoreaux/environmental-sound-classification-50") dataset.

This repository uses `librosa` library to convert sound wave to digital audio signal and then converts that singal to spectrogram. This spectrogram is then sent to proposed CNN model. The CNN model is implemented using `Tensorflow`, it has 6 convolutional layers, 3 max pooling layers and 2 fully connected layers. The model is divied into 3 convolutional blocks. Each block has convolutional layer, max pooling layer and convolutional layer in sequence. Below is the screenshot of model summary.

![model summary]("https://drive.google.com/file/d/14V4jYMTIbFtPzm5cZcHMcc_t32fE_JCu/view?usp=share_link")

This repository contains 6 files. The `implementation.ipynb` is the implementation code of the model, the `custom.ipynb` is to load the model and run it on custom audio file, the `requirments.txt` is the txt file containing requirments to run the model, the `categories.csv` contains categories of classification and the `instructions.txt` contains instructions to better understand this repository.

# Highlights

The input is audio file. Here is the audio input given to the model.

The spectrogram generated is 

And the model categorized it as `rain` sound.

# Prerequisites

`Python>=3.6`

# Getting started

1. Download the repository and unzip it.
2. Install necessary packages using `pip install -r requirements.txt`.
3. Read the `instructions.txt` for better understanding of repository.

# Future work

In future, i'm looking forward to train CNN model based on inception network and residual network and to improve model's accuracy.
