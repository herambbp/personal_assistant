# Personal AI Assistant

This is a Python script that implements a personal AI assistant using various libraries and APIs. The assistant can perform tasks such as answering questions, opening websites, playing music, providing the current time, and performing Google searches.

## Prerequisites

Before running the script, make sure you have the following libraries and APIs installed:

- `speech_recognition`: Library for performing speech recognition
- `os`: Library for interacting with the operating system
- `win32com.client`: Library for text-to-speech conversion
- `webbrowser`: Library for opening websites
- `datetime`: Library for working with dates and times
- `openai`: Library for accessing the OpenAI API

You will also need an API key from OpenAI to use the OpenAI GPT-3.5 model for generating responses. Replace the placeholder `"API KEY of open ai"` in the code with your actual API key.

## Usage

1. Import the necessary libraries:

```python
import speech_recognition as sr
import os
import win32com.client
import webbrowser
import datetime
import openai
```

2. Set up the speaker for text-to-speech conversion:

```python
speaker = win32com.client.Dispatch("SAPI.SpVoice")
```

3. Define the function for interacting with the AI model:

```python
def ai(query):
    openai.api_key = "API KEY of open ai"  # Replace with your actual API key
    # Rest of the code
```

4. Define the function for the assistant to speak:

```python
def say(text):
    speaker.speak(text)
```

5. Define the function for capturing user commands:

```python
def takeCommand():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        r.pause_threshold = 0.8
        audio = r.listen(source)
        try:
            print("Recognising...")
            query = r.recognize_google(audio, language="en-in")
            print(f"User said {query}")
            return query
        except Exception as e:
            return "Some error occurred...Sorry!"
```

6. Start the assistant and enter a continuous loop to listen for user commands:

```python
say("Hello, I am Personal AI Assistant")
while True:
    while True:
        print("Listening...")
        query = takeCommand()
        say(query)
        
        # Perform various tasks based on user commands
        
        print(f"Query: {query}")
        ai(query)
```

7. Perform tasks based on user commands:

- Open websites: The assistant can open YouTube, Flipkart, and Wikipedia.

```python
sites = [["youtube", "https://youtube.com"], ["flipkart", "https://flipkart.com"], ["wikipedia", "https://wikipedia.com/"]]
for site in sites:
    if f"open {site[0]}" in query.lower():
        webbrowser.open(site[1])
```

- Play music: The assistant can play a specific music file.

```python
if "open music" in query.lower():
    musicpath = r"motivational-electronic-distant-132919.mp3"
    os.system(musicpath)
    break
```

- Get the current time:

```python
if "tell time" in query.lower():
    strftTime = datetime.datetime.now().strftime("%H : %M")
    say(f"The time now is {strftTime}")
    break
```

- Perform Google searches: The assistant can perform a Google search based on user input.

```python
if "google search" in query.lower():
    say("What do you want to Google search?")
    search = takeCommand()
    webbrowser.open

(f"https://www.google.com/search?q={search}")
    break
```

- Open Zoom: The assistant can open the Zoom application.

```python
if "open zoom" in query.lower():
    os.system(r"C:\Users\Pratiksha\AppData\Roaming\Zoom\bin\Zoom.exe")
    break
```

- Generate AI-based responses: For all other queries, the assistant uses the OpenAI GPT-3.5 model to generate responses.

```python
print(f"Query: {query}")
ai(query)
```

Note: You may need to customize the paths and commands based on your specific system setup.

## Contributing

Feel free to contribute to this project by making improvements or adding new features. You can submit a pull request with your changes, and they will be reviewed and merged accordingly.

