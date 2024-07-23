# AudFake AI Audio Generator

This project demonstrates how to achieve real-time audio processing in Python. The script captures audio input from the microphone, converts the spoken words to text using Google's speech recognition service, and then synthesizes the recognized text into speech using a different voice. The primary libraries used for this project are `SpeechRecognition` and `pyttsx3`.

## Features

- Real-time audio capture from the microphone
- Speech-to-text conversion using Google's speech recognition service
- Text-to-speech conversion with customizable voices

## Requirements

- Python 3.x
- `SpeechRecognition` library
- `pyttsx3` library

## Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/real-time-audio-processing.git
   cd real-time-audio-processing
   ```

2. **Install the required libraries:**
   ```bash
   pip install SpeechRecognition pyttsx3
   ```

3. **Ensure you have `pyaudio` installed.** If not, you can install it via pip:
   ```bash
   pip install pyaudio
   ```
   *Note: On some systems, you may need additional steps to install `pyaudio`. Refer to the official documentation or use system-specific package managers.*

## Usage

1. **Run the script:**
   ```bash
   python real_time_audio_processing.py
   ```

2. **Speak into the microphone:**
   The script will prompt you to say something. It will capture your speech, convert it to text, and then output the text as speech using a different voice.

## Code Overview

```python
import speech_recognition as sr
import pyttsx3

# Initialize the speech recognition engine
recognizer = sr.Recognizer()

# Initialize the text-to-speech engine
engine = pyttsx3.init()

# Set the properties for the text-to-speech engine (e.g., voice)
voices = engine.getProperty('voices')
# You can choose a different voice here, e.g., voices[1] for a different voice
engine.setProperty('voice', voices[0].id)

# Function to process audio in real-time
def process_audio():
    with sr.Microphone() as source:
        print("Say something...")
        while True:
            try:
                audio_data = recognizer.listen(source, timeout=None)
                text = recognizer.recognize_google(audio_data)
                print("You said:", text)
                
                # Convert text to speech with a different voice
                engine.say(text)
                engine.runAndWait()
            except sr.UnknownValueError:
                print("Could not understand audio")
            except sr.RequestError as e:
                print("Error retrieving speech recognition results; {0}".format(e))

# Call the function to start real-time processing
process_audio()
```

## Customization

- **Changing the voice:**
  The script uses the first available voice by default. You can change the voice by selecting a different index from the `voices` list:
  ```python
  engine.setProperty('voice', voices[1].id)
  ```
  Use a different index to choose another voice available on your system.

## Troubleshooting

- **Speech recognition errors:**
  Ensure you have a stable internet connection since the speech recognition service relies on Google's API.
  
- **PyAudio installation issues:**
  Refer to the [PyAudio documentation](https://people.csail.mit.edu/hubert/pyaudio/#downloads) for system-specific installation instructions.

### Reference Link
https://github.com/CorentinJ/Real-Time-Voice-Cloning

https://github.com/smoke-trees/Voice-synthesis

https://github.com/Suhee05/Text-Independent-Speaker-Verification

https://github.com/kingridda/voice-cloning-AI

https://github.com/PaddlePaddle/PaddleSpeech

https://github.com/jackaduma/CycleGAN-VC2

https://github.com/deterministic-algorithms-lab/Cross-Lingual-Voice-Cloning

https://github.com/jackaduma/CycleGAN-VC2

https://github.com/ming024/FastSpeech2 
