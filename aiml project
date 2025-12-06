import random
import datetime
import os
import webbrowser
import sys

greeting_phrases = [
    "Yes sir, at your service!", 
    "Right away sir!", 
    "Certainly sir!",
    "As you wish sir!", 
    "Working on it sir!"
]

def speak(text):
    print(f"🟦 JARVIS: {text}")

def get_time():
    now = datetime.datetime.now()
    time_str = now.strftime("%I:%M %p")
    return time_str

def search_web(query):
    url = f"https://www.google.com/search?q={query}"
    webbrowser.open(url)
    speak(f"Searching for {query}")

def open_app(app_name):
    if "youtube" in app_name:
        webbrowser.open("https://youtube.com")
        speak("Opening YouTube")
    elif "google" in app_name:
        webbrowser.open("https://google.com")
        speak("Opening Google")
    elif "notepad" in app_name:
        os.system("notepad")
        speak("Opening Notepad")
    else:
        speak("Application not found")

def process_command(command):
    command = command.lower()
    
    if any(word in command for word in ["time", "clock"]):
        current_time = get_time()
        speak(f"The time is {current_time}")
    
    elif "search" in command or "google" in command:
        query = command.replace("search", "").replace("google", "").strip()
        if query:
            search_web(query)
        else:
            speak("What would you like me to search?")
    
    elif any(word in command for word in ["open", "launch"]):
        app = command.replace("open", "").replace("launch", "").strip()
        open_app(app)
    
    elif "who is" in command or "what is" in command:
        topic = command.replace("who is", "").replace("what is", "").strip()
        speak(f"Accessing knowledge base about {topic}")
        webbrowser.open(f"https://en.wikipedia.org/wiki/{topic.replace(' ', '_')}")
    
    elif "system" in command or "computer" in command:
        speak(f"You are running Python {sys.version.split()[0]}")
    
    elif any(word in command for word in ["hello", "hi", "hey"]):
        speak(random.choice(greeting_phrases))
    
    elif any(word in command for word in ["exit", "bye", "quit"]):
        speak("Shutting down JARVIS. Goodbye sir!")
        return False
    
    else:
        speak("Command not recognized. Try: time, search, open youtube, who is Einstein")
    
    return True

def jarvis_main():
    speak("J.A.R.V.I.S. online. How may I assist you sir?")
    
    while True:
        command = input("Sir: ").strip()
        
        if not process_command(command):
            break

if __name__ == "__main__":
    jarvis_main()
