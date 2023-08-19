# About

## Abstract

This repository proposes a Convolutional Neural Network (CNN) model which recognises sound from 50 different categories including nature sound, human non speech sound, urban sound, etc. with **70% accuracy**. The wav file is processed and converted into spectrum of size (11,220) and model classifies each spectrum according to label.

## Detailed

The model is trained on [esc50]("https://www.kaggle.com/datasets/mmoreaux/environmental-sound-classification-50") dataset which contains 2002 wav files of 50 different categories including nature sound, animal sound, human non speech sound, urban sound, domestic sound, bird sound, etc. The wav file is converted into spectrum of shape (11,220) and the model is trained on this spectrum.

This repository uses `librosa` library to read wav file at the sample rate of 44100 Hz. Each wav file has 2205000 samples. This repository uses first 220000 samples and creates 220 spectrograms with window size of 1000. Hence each spectrogram is of size 1000 samples and there are such 220 spectrograms, now each spectorgram is divided into 11 different channels. The perticular channel takes first and last k points and processes with whole spectrogram. Hence for one spectrogram containing 1000 samples, it has different values for each channels, there are 11 channels total so one spectrogram is divided into 11 points and there are total 220 spectrograms. Hence ultimelty we get the spectrum of shape (11,220). This spectrum is for one wav file.

Now for each wav file the spectrum is created and saved in form of numpy array into `CSV`. This `CSV` is the training dataset for model. The proposed `CNN` model has 6 convolutional layers, 3 pooling layers, 2 fully connected layers with selu activation.

This repository contains 8 files. The `implementation.ipynb` is the implementation code of the model, the `custom.ipynb` is to load the model and run it on custom wav file, the `wav2spectrogram.ipynb` reads the wav file and convert into spectrogram, the `wav2spectrum.ipynb` reads the wav and converts it into processed spectrum, the `requirments.txt` is the txt file containing requirments to run the model, the `categories.csv` contains categories of classification and the `instructions.txt` contains instructions to better understand this repository.

# Highlights

The model structure is : 

<img width="493" alt="Screenshot 2023-04-04 at 9 59 08 AM" src="https://user-images.githubusercontent.com/76246981/230334455-7ba1f1e5-6dd3-4af7-8930-91cf484ce1c0.png">

The input is audio file. Here is the audio input given to the model.

<a href="https://drive.google.com/drive/u/1/folders/1mW_QaB1f0xdvfTTPvoRR1k393CN_DzdC">Audio file</a>

The spectrogram generated is 

<img width="540" alt="Screenshot 2023-04-04 at 9 47 34 AM" src="https://user-images.githubusercontent.com/76246981/230334705-912799b3-9e9a-4e14-8086-a77097f2490b.png">

And the model categorized it as `rain` sound.

# Prerequisites

`Python>=3.6`

# Getting started

1. Download the repository and unzip it.
2. Install necessary packages using `pip install -r requirements.txt`.
3. Read the `instructions.txt` for better understanding of repository.

# Future work

In future, i'm looking forward to train CNN model based on inception network and residual network and to improve model's accuracy.

# Connect with me

Give your feedback at : karanhadiyal65@gmail.com
