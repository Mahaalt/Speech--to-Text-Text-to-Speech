# Speech to Text and Text to Speech

### The Requirements

* Python

* IBM Watson

---
### Installation
   
    pip install pipwin
    pipwin install pyaudio
    pip install -r requirments.txt
    pip install ibm_watson
    
---
### Speech to Text

1. Go to this link [IBM Cloud](https://cloud.ibm.com/), Search for Speech.

2. Select your location, for example London, then press on create button.

3. Choose Service Credentials from left hand side, Open the auto-generated Service Credentials, Copy the api-key and copy your location or region.

4. Open your CMD and clone this link https://github.com/IBM/watson-streaming-stt.

5. Open any python editor like VS Code, Change speech.cfg.example file into speech.cfg and paste the apikey in it and paste the region.

6. Open the Terminal, Install all the instalation.

7. Go to transcribe.py file, and change the model into your by this link https://cloud.ibm.com/docs/speech-to-text?topic=speech-to-text-models.

8. Finally you can run your program using this command python transcribe.py -t 10

---
### Text to Speech

1. Open the transcribe.py file, type this code under the imports:

       from ibm_watson import TextToSpeechV1
       from ibm_cloud_sdk_core.authenticators import IAMAuthenticator

       authenticator = IAMAuthenticator('vYI9rkcSWl_wELYNt2Y-5uxAuNDmPKL9XkMLal4R0Vn1')
       tts = TextToSpeechV1(authenticator=authenticator)
       tts.set_service_url('https://api.us-south.text-to-speech.watson.cloud.ibm.com/instances/4afce834-c1d1-4edf-ba89-dafcd89544a0')
    
 2. Open the Terminal, type this command:
 
        pip install ibm_watson
        
 ---  
 
 ### Audio File
    
To create an audio,mp3 file, type this code inside read_audio function:

    with open('text.txt', 'r') as f:
    text = f.readlines()
    text = [line.replace('\n','') for line in text]
    text = ''.join(str(line) for line in text)
    with open('./voice.mp3', 'wb') as audio_file:
    res = tts.synthesize(text, accept='audio/mp3', voice='en-GB_JamesV3Voice').get_result()
    audio_file.write(res.content)
---

### Text File

1. Create the text.txt file, make it in the same file with transcribe.py file.

2. Go to the on_message function and type this code:
   
       with open('text.txt', 'w') as out:
       out.writelines(data['results'][0]['alternatives'][0]['transcript'])
       
  ---
  
  ### Output
  
  * Text result:
  ![image](https://user-images.githubusercontent.com/71232960/128470474-6a096de5-9241-4e84-be86-a3b52a30bac3.png)
  
  * Audio result:
 
   https://user-images.githubusercontent.com/71232960/128471251-e84c35c9-d70d-4db9-9fe2-dd234cc00701.mp4

---

### The Sources
* https://youtu.be/YCyuZM454_I
* https://youtu.be/A9_0OgW1LZU
