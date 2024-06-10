# Instrument Classifier
# Goal & metrics 
The goal of this project was to create an instrument classifier model that can accurately predict any given audio file and return the correct instrument. For this project's scope, I chose five unique instrument samples that are standard in music production: kick, snare, 808, open hat, and closed hat. Coming from an audio and music background, I was curious to explore the many features that could distinguish an instrument. My metrics for this project were the accuracy score of the MLP, Random forest, and Convolutional Neural Network.

# Data

Background on data: The following data includes 2065 audio samples ( Kicks, Snares, 808's, Open hats, and Closed hats) from my music production library. This library was collected from several sources, including but not limited to music production/sample-sharing websites such as Landr, Splice, Reddit, etc. The audio library can be accessed [Here](https://drive.google.com/drive/folders/1Dl2wvDMLQip063K0ncE7Anv7zzn25a0L?usp=sharing). Some of the sounds also came from the [Drum classifier github project](https://github.com/aabalke33/drum-audio-classifier/tree/main). These audio samples are typically a few seconds (0-4 seconds) in WAV File formats. I am exploring how to convert these samples into their features, including arrays of time, pitch, and amplitude, to train the mode to accurately classify the instruments based on any given audio sample in or outside of this library. Before working with data, I reviewed the unique audio files to ensure data integrity and assumptions made in the beginning stage. This will be explored further in the cleaning section.

---
### Data Dictionary ###


| Feature | Type | Dataset | Description |
|---------|------|---------|-------------|
|**File_path**|*str*| My data | The file path or directory where the audio file is located.|
|**File_name**|*str*| My data | The name of the file, including the file extension. |
|**Instrument**|*str*| My data | The name of the instrument. Instruments are: Kick, Snare, 808, Open hat, Closed hat|
|**End_time**|*datetime*| My data | The timeframe in seconds that the audio sample ends |
|**Index**|*int*| My data | An index value assigned for instrument based on the instrument column. |
|**Instrument_encoded**|*int*| My data | An encoded value representing the instrument type. |
|**Instrument_0**|*int*| My data | A binary indicator (0 or 1), representing whether the sample is a Kick drum or not.|
|**Instrument_1**|*int*| My data | A binary indicator (0 or 1), representing whether the sample is a Snare drum or not. |
|**Instrument_2**|*int*| My data | A binary indicator (0 or 1),representing whether the sample is an 808 drum or not. |
|**Instrument_3**|*int*| My data | A binary indicator (0 or 1), representing whether the sample is an Open hat or not. |
|**Instrument_4**|*int*| My data | A binary indicator (0 or 1), representing whether the sample is a Closed hat or not. |

### Important Vocabulary Dictionary
**dB/Decibels:** Mesurable units of levels in sound pressure.

**Pitch:** Human perception of frequency that orders the frequency sound wave on a scale (Example: Music notation, C, D, E etc).

**Frequency:** Measurable rate of vibration (Measured through Hz or hertz).

**Amplitude:** Magnitude of a waveform.

**Time:** Measurable timeframe of an audio sample. For the purpose of this project, seconds are more commonly used.

**Sample:** The audio file sample.

**808:** A percussive sound is known for its low-frequency bass and distinct booming sound (named based on the classic Roland TR-808 drum machine).

**Kick:** A bass drum part of a drum kit is typically played by stepping on a pedal attached to a mallet.

**Snare:** A percussion instrument that produces a staccato sound when hit.

**Open Hat:** A percussive instrument that consists of the top and bottom cymbals being separated.

**Closed Hat:** A percussive instrument that consists of the top and bottom cymbals being pressed tightly together.

Models:

**MLP:** A Multilayer perceptron is an artificial neural network consisting of many layers of neurons that can be used to learn complex patterns in data.

For more sources, review the technical terms in the appendix.

---

# Executive Summary:

### Findings.
From my findings, all three models obtained the same accuracy score of 1.0. Because of this, I decided to pick the model most suitable for my current audio data and for how I preprocess and feature-engineered my audio data through one hot encoding of each of my instruments with Keras's one hot encoder. In this case, the MLP model was the best choice for predicting my audio data and how my data is currently set up.

In the future, I will continue working with CNN because, based on my EDA/image representation of my samples and how CNN can process audio data, I believe CNN has the most potential for future growth in the project.

Through this experience, I learned that while CNN can be utilized with audio data samples, feasibility, such as computational power for audio conversions and preprocessing, is crucial to ensuring that the CNN model works accurately with the audio data. In this particular case, processing the audio directly required more computational power. From this, I researched and found a more suitable model for preprocessing my audio data and utilized a more appropriate model, MLP. This neural network with foundational architecture in deep learning can be used for various machine learning tasks, including classification problems and audio data.

My MLP model obtained an accuracy score of one and was overfit based on the accuracy score. While the loss is decreasing, the accuracy is increasing gradually, and the model seems to be able to predict the validation set accurately; this happened quickly, which could be considered an issue. I noticed that the training and validation losses were similar numerically. For example, the values 0.0025 and 0.0020 showed that it interpreted and processed the data. 

For the CNN, I had a test set loss of approximately 0.0061 and a test set accuracy of 1.0 with a default epoch value of 10. Some key findings are that the loss and accuracy are decreasing gradually. The model is also able to predict the validation set accurately. However, the model overfits a bit due to the negative validation loss of 0.0066 at epoch 5.

For my Random Forest, I had very similar results as well with an accuracy of 1.0. The model was able to get 94 true positives for kicks, 104 true positives for 808s, 58 true positives for snares, 96 true positives for open hat and 50 true positives for closed hat. While this is a decent result, I did not look into the other measures such as recall or other scores since I received a similar result as the result of my models.


# If you are interested in viewing even more ...

Interactive Instrument classifier based on my model web app (CURRENTLY IN PROGRESS): https://instrumentclassifier.streamlit.app/


# Sources:

www.perplexity.ai , 2024, Sited in EDA

https://github.com/aabalke33/drum-audio-classifier/tree/main, 2023: Gave me a good starting point for framework and helped when creating the loading application that can input file path for model prediction.

https://towardsdatascience.com/cnns-for-audio-classification-6244954665ab, 2023: Gave me more insight in CNN audio modeling. Sited in EDA

https://www.vocabulary.com/dictionary/pitch, 2024. Sited in EDA

Teachmeaudio.com, 2024, Sited in EDA
