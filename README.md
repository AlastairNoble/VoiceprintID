# Voiceprint-Identification
A general overview of the Voiceprint Identification project is attached HERE. This paper outlines a bried introduction to the project, the teams methodology, results and discussion, and conculsions/future work. For information regarding how to use the application, view the *How To Use* section. A more in-depth description about how the model works is also in the *How It Works* setion below.

<a href="VoicePrintIdentificationPaper.pdf" class="image fit"><img src="images/marr_pic.jpg" alt=""></a>

## How To Use
### GUI
The GUI is Tkinter-based for real time classification. 

<img src="https://user-images.githubusercontent.com/65412039/111880975-be84e180-8984-11eb-8b48-c8d314fd8c11.png" width="340">

#### Add a User Profile
Add a user profile by simply typing the user name and pressing the *Add User* button. The GUI will then guide you through the process of adding a user by prompting you to say a couple sentences and recording your data. If the recording time is too long or short, feel free to change the *RECORD_SECONDS* variable in the *GUI.py* file on line 125.
Add a user profile by simply typing the user name and pressing the *Add User* button. The GUI will then guide you through the process of adding a user by prompting you to say a couple sentences and recording your data. Thats it! Now, once you train the model again to train with your data, the model can guess you. To train the model, just simply press the *Train Model* Button and wait until the model fully trains. Once the model has trained, the validation accuracy of the model will be updated on the UI and you wil be ready to record live!

#### Guess Who is Speaking Live
After adding all of the neccecary user profiles and pressed the train model button, make sure to press the *big red microphone* button to start recording. Now, your microphone will be picking up live data, funnelling to the model, and produced a result of who is speaking. In the list of names on the left hand side of the UI, it will highlight the person who is speaking's name.

<img src="https://user-images.githubusercontent.com/65412039/111881794-96977d00-8988-11eb-8a7b-054cc04138b3.png" width="340">

In this image, the model is 80% sure that Alex is speaking on a model that has the validation accuracy of 96.2%

#### Save/Load Model
Once you are all done speaking for the day, done forget to save your model before you exit to avoid retraining your data. Do this by pressing *Save Model* once a model has been trained. After 

## How It Works
### Model
The word model trains a keras sequential on files in the 'words' folder. To train a model on audio data, use file structure words/'word'/'name'/'file'.wav (ex words/the/john/1.wav) and call word model as follows
```python
words = ["alexa","the", "be", "to", "of", "and"]
model = word_model(words)
```
this should output

Epoch 1/50
5/5 [==============================] - 0s 63ms/step - loss: 1.7061 - accuracy: 0.3459 - val_loss: 0.7850 - val_accuracy: 0.8491  
.  
.  
.  
Epoch 50/50
5/5 [==============================] - 0s 33ms/step - loss: 0.0259 - accuracy: 0.9937 - val_loss: 0.0223 - val_accuracy: 0.9811  
  
and make predictions by calling *predict_speaker*
```python
name, confidence = predict_speaker("test/eli.wav", model)
# 'eli', .9099897
```
this outputs the name and confidence

### Data Collection
### Libraries
Model | GUI | Misc
| :---: | :---: | :---:
Keras | TKinter | Wave
Librosa | PyAudio | OS
Speech Recognition  | PyDub | Time
SkLearn  |  | Shutil
Pandas  |  | Math
Tensorflow  |  | 
