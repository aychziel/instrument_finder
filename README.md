# Instrument Classifier
# Goal & metrics 
The purpose of this project was to create an instrument classifier model that can accurately predict any given audio file and return the correct instrument. For the scope of this project I chose five unique instruments which are common in music production which include kick, snare, 808, open hat, and closed hat.  Coming from an audio and music background, I was curious in exploring the many factors that could distinguish an instrument. My metrics for this project was the accuracy score of which ever models I choose which in this case it was the MLP, Random forest and for the purposes of testing, the Convolutional Neural Network. For context, Convolutional Neural Networks is a deep learning model commonly used for image classification tasks.

# Data

 ### Background on data: The following data includes 2065 audio samples ( Kicks, Snares, 808's, Open hats, and Closed hats) from my own music production library which is made from several sources which include but are not limited to music production/sample sharing websites such as Landr, Splice, Reddit etc. The audio library can be accessed [Here](https://drive.google.com/drive/folders/1Dl2wvDMLQip063K0ncE7Anv7zzn25a0L?usp=sharing). Some of the sounds also came from the [drum classifier github project](https://github.com/aabalke33/drum-audio-classifier/tree/main). These audio samples are typically a few seconds (0-4 seconds) in WAV File formats. I am looking to explore how to convert these samples into their own features which include arrays of time, pitch, and amplitude to train the mode to accuratley classify the instruments based on any given audio sample in this library or outside of this library. Before starting to work with data, I decided to review the unique audio files to ensure data integrity and assumption made as far as the beginning stage. This will be explored further in the cleaning section.
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


---

To start, I want to create a dataframe that has the following columns: File_path, File_name, Instrument, Start_time and End_time. While I have
thought about labeling this a "drum classfier" meaning that my column would have technically been "Drums", I decided to keep it general to instrument because I am intrested in exploring this model in the future with various intruments.

I may assign variable where I drop some of these columns later in the process but for organizational purposes, I am intrested in making this my main df and saving it as such.

# Executive Summary:

### Findings.
From my findings, the models all had similar results so there wasnt neccesarily a best model for the purposes of the project so becuase of this, I decide to pick the model with the most potential for future growth which would be the CNN.

Something import to note however is that, for the purposes of which model was the most accurate to the data that I have, I ended up picking another neural network model, MLP, in addition to the other models that I made which included Random forest, CNN. This particular problem is a multiclass classification problem because it has many classes that require classification.

Through this experience I learned that while the CNN is possible to acheive correctly, the feasibility of this is a bit difficult due to computational power of the audio conversions which require more RAM and in general can be time extensive. I had this issue which led me to formatting my CNN model incorrectly and applying the one hot encoding to the CNN model which is not the appropriate way of classification. Learning from this, I did more research and applied a more appropriate model, MLP which mentioned previously is a neural network that has foundational architecture in deep learning and is used for various machine learning tasks, including classification.

As for my results with the MLP model, from my findings, the model is also overfit due to the accuracy score. While the loss is decreasing and the accuracy is increasing gradually and the model seems to able to accurately predict the validation set, this happens at a very fast rate which could be considered an issue. Something else I noticed is that the training and validation losses are similar numerically for example, 0.0025 and 0.0020 which could mean that it is working well and interpreting the data. There are many things that could be affecting this model however, I think that with more data and also different parameters this could potentially improve.

As for The CNN model, I had a test set loss of approx 0.0061 and a test set accuracy of 1.0 with default epoch value of 10 and .Some key finding from this is that the loss is decreasing and the accuracy is increasing gradually and the model is able to accurately predict the validation set however, the model overfits a bit due to the negative validation loss at 0.0066 at epoch 5.

For my Random Forest, I had very similar results as well with an accuracy of 1.0. The model was able to get 94 true positives for kicks, 104 true positives for 808s, 58 true positives for snares, 96 true positives for open hat and 50 true positives for closed hat. While this is a decent result, I did not look into the other measures such as recall or other scores since I received a similar result as the result of my models.


If youre intrested in viewing even more...

Interactive Instrument classifier based on my model web app (in progress): https://instrumentclassifier.streamlit.app/


Sources:
www.perplexity.ai , 2024, Sited in EDA

https://github.com/aabalke33/drum-audio-classifier/tree/main, 2023: Gave me a good starting point for framework and helped when creating the loading application that can input file path for model prediction.

https://towardsdatascience.com/cnns-for-audio-classification-6244954665ab, 2023: Gave me more insight in CNN audio modeling. Sited in EDA

https://www.vocabulary.com/dictionary/pitch, 2024. Sited in EDA

Teachmeaudio.com, 2024, Sited in EDA

https://www.geeksforgeeks.org/python-keras-keras-utils-to_categorical/

https://www.tensorflow.org/api_docs/python/tf/keras/utils/to_categorical

https://machinelearningmastery.com/multi-class-classification-tutorial-keras-deep-learning-library/
