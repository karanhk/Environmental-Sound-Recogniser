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

The audio of keyboard typing sound : 

<a href="https://drive.google.com/file/d/1HzEGcBEzgElgmD3dFsvwIUpax3AMrfWY/view?usp=sharing">Audio file</a>

The waveform : 

![waveform](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/4757eb37-af85-4559-bd97-792d235b4ccd)

The spectrogram : 

![spectrogram](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/d4de9aab-de69-443e-8276-c22ba7cc61dd)

The processed spectrum :

![spectrum](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/dbdaafb7-443b-4195-ad7c-0cae708c6e99)

# Prerequisites

`Python>=3.6`

# Getting started

1. Clone the repository.
2. Install necessary packages using `pip install -r requirements.txt`.
3. Run the `custom.ipynb` file to use the pretrained model on custom wav file, change path of model and wav file accordingly.
4. Read the `instructions.txt` for better understanding of repository.

# Future work

In future, i'm looking forward to train CNN model based on inception network and residual network and to improve model's accuracy.

# Connect with me

Give your feedback at : karanhadiyal65@gmail.com
