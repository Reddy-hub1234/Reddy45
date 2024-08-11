# Define a dictionary for user preferences
preferences = {
    "greetings": ["hello", "hi", "hey"],
    "play_music": ["play music", "play song", "play audio"],
    "open_app": ["open app", "launch application", "start program"]
}

# Define a function for voice input
def get_voice_input():
    with sr.Microphone() as source:
        audio = r.listen(source)
        try:
            voice_input = r.recognize_google(audio)
            return voice_input.lower()
        except sr.UnknownValueError:
            return ""
        except sr.RequestError:
            return ""

# Define a function for task automation
def automate_task(task):
    if task in preferences["greetings"]:
        print("Hello! How can I assist you today?")
    elif task in preferences["play_music"]:
        os.system("start music_player.exe")
    elif task in preferences["open_app"]:
        os.system("start app.exe")  
    else:               
        print("Sorry, I didn't understand. Please rephrase.")

# Main program loop
while True:
    voice_input = get_voice_input()
    automate_task(voice_input)
