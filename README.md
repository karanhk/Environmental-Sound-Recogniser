# About

## Abstract

This repository proposes a Convolutional Neural Network (CNN) based model which recognises sound of 50 different categories including nature sound, human non speech sound, urban sound, etc. with **70% accuracy**. The model reads processed spectrum of wav file and predicts the label. The wav file is processed and converted into spectrum of size (11,220) and model classifies each spectrum according to label.

This repository contains 8 files. The `implementation.ipynb` is the implementation code of the model, the `custom.ipynb` is to load the model and run it on custom wav file, the `wav2spectrogram.ipynb` reads the wav file and convert into spectrogram, the `wav2spectrum.ipynb` reads the wav and converts it into processed spectrum, the `requirments.txt` is the txt file containing requirments to run the model, the `categories.csv` contains categories of classification and the `instructions.txt` contains instructions to better understand this repository.


## Detailed

The model is trained on [esc50]("https://www.kaggle.com/datasets/mmoreaux/environmental-sound-classification-50") dataset which contains 2002 wav files of 50 different categories including nature sound, animal sound, human non speech sound, urban sound, domestic sound, bird sound, etc. The wav file is converted into spectrum of shape (11,220) and the model is trained on this spectrum. Below is the step by step explaination of respository.


### The model : 

The proposed Convolutional Neural Netowrk (CNN) based model has 6 convolutional layers, 3 pooling layers, 2 fully connected layers, 1 dropout layer with selu activation. The model taks spectrum of wav file in the form of numpy array of size (11,220) as an input and gives probability for each class in vector of size (50,1). Below is the screenshot of model's summary.

![model_summary](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/e3840f08-c9cb-46a7-aee9-a84ab9c59e55)

### Wav to Spectrum : 

Before jumping into how to create spectrum, let us first understand the structure of wav file and how it is read in Python. The wav file is collection of samples like image is collection of pixels. The sample rate is the number of sample used per second to record analog audio and store in the form of digital audio. Here the sample rate is 44100 Hz and each wav file is of 5 seconds, so each wav file has 220500 samples. The wav to spectrum follows the path : Wav -> Waveform -> Spectrogram -> Spectrum.

The wav file of keyboard typing sound : <a href="https://drive.google.com/file/d/1TZlnt31opbRcwqSYLFSXRiQz_BVP7hJL/view?usp=sharing">Wav file</a>

Now let us understand wav to waveform. The waveform is the distribution of amplitude vs time of wave file. We read wavefile in form of numpy array of size (220500,1) so first 440100 samples are for first second and second 440100 samples are for the 2nd second and so on. we divide the array by sample rate and get the array of shape (44100,5). The value at perticular index represents the amplitude, we plot the array to get the waveform. Below is the screenshot of the waveform. 

![waveform](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/4757eb37-af85-4559-bd97-792d235b4ccd)

The spectrogram is the colour map of distribution of frequency (in Hz) vs time (in s) where the color represents the intensity (in dB). By using `librosa` library's `spectrogram` method we the frequency, time and intensity. Here is the plot of spectrogram.

![spectrogram](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/d4de9aab-de69-443e-8276-c22ba7cc61dd)

Now the question is why do we need to create spectrum, can't we train model on spectrogram ? The answer is the spectrogram is very large, it is of the shape (44100,5). If we train model on spectrogram the model will have too many parameters and will become too much complex. And secondly this spectrogram contains noises we need to filter the spectrogram. So we convert this spectrogram into spectrum of shape (11,220).

To convert spectrogram into spectrum we take first 220000 samples of wav file, and we create 220 spectrograms of 1000 samples. The one spectrogram contains 1000 samples, we divide this spectrogram into 11 different channels. The one channel processes first k and last k samples with the spectrogram and produces the float number. So from one spectrogram we have 11 different channles, so the spectrogram of 1000 samples is divided into vector of size (11,1). We have 220 such spectrograms, so ultimetly this 220 spectrograms gets converted into array of size (11,220). This array is for one wav file. This is how we convert wav file of 440100 samples into array of (11,220). This is the input for model. Below is the screenshot of spectrum.

![spectrum](https://github.com/karanhk/Environmental-sound-recognition/assets/76246981/dbdaafb7-443b-4195-ad7c-0cae708c6e99)


# Prerequisites

`Python>=3.6`

# Getting started

1. Clone the repository or download the zip file.
2. Install necessary packages using `pip install -r requirements.txt`.
3. Run the `custom.ipynb` file to use the pretrained model on custom wav file, change path of model and wav file accordingly.
4. Read the `instructions.txt` for better understanding of repository.

# Future work

In future, i'm looking forward to train CNN model based on inception network and residual network and to improve model's accuracy.

# License

This project is licensed under the Apache 2.0 License - see the <a href="https://github.com/karanhk/Environmental-Sound-Recogniser/blob/main/LICENSE">LICENSE</a>
file for details

# Connect with me

Give your feedback at : karanhadiyal65@gmail.com
