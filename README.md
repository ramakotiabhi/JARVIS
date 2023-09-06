# THE PROJECT AIM

The project aims to develop a personal-assistant for Linux-based systems. Jarvis draws its inspiration from virtual assistants like Cortana for Windows, and Siri for iOS. It has been designed to provide a userfriendly interface for carrying out a variety of tasks by employing certain well-defined commands. Users can interact with the assistant either through voice commands or using keyboard input. As a personal assistant, Jarvis assists the end-user with day-to-day activities like general human conversation, searching queries in google, bing or yahoo, searching for videos, retrieving images, live weather conditions, word meanings, searching for medicine details, health recommendations based on symptoms and reminding the user about the scheduled events and tasks. The user statements/commands are analysed with the help of machine learning to give an optimal solution.

# INTRODUCTION

## J.A.R.V.I.S. (Just A Rather Very Intelligent System)

**J.A.R.V.I.S. (Just A Rather Very Intelligent System)** is a fictional character voiced by Paul Bettany in the Marvel Cinematic Universe (MCU) film franchise, based on the Marvel Comics characters Edwin Jarvis and H.O.M.E.R., respectively the household butler of the Stark family and another AI designed by Stark. J.A.R.V.I.S. is an artificial intelligence created by Tony Stark, who later controls his Iron Man and Hulkbuster armor for him. In Avengers: Age of Ultron, after being partially destroyed by Ultron, J.A.R.V.I.S. is given physical form as Vision, physically portrayed by Bettany. Different versions of the character also appear in comics published by Marvel Comics, depicted as AI designed by Iron Man and Nadiavan Dyne.

## PROBLEM STATEMENT

We are all well aware about Cortana, Siri, Google Assistant and many other virtual assistants which are designed to aid the tasks of users in Windows, Android and iOS platforms. But to our surprise, there’s no such virtual assistant available for the paradise of Developers i.e. Windows platform.

## AGENDA OF THE PROJECT

This Software aims at developing a personal assistant for windows. (LAMDA) The main purpose of the software is to perform the tasks of the user at certain commands, provided in either of the ways,speech or text. (LAMDA) It will ease most of the work of the user as a complete task can be done on a single command.

## ELEMENTS OF PROJECT

**COMMANDS USED:**

1. **pyttsx3**: pyttsx is a cross-platform text to speech library which is platform-independent. The major advantage of using this library for text-to-speech conversion is that it works offline. To install this module, type the below command in the terminal:
                                                                                              
                                                                                                *pip install pyttsx3*

2. **SpeechRecognition**: This allows us to convert audio into text for further processing. To install this module, type the below command in the terminal:
                                                                                            
                                                                                            *pip install SpeechRecognition*

3. **pywhatkit**: This is an easy-to-use library that will help us interact with the browser very easily. To install the module, run the following command in the terminal:
                                                                                                
                                                                                                *pip install pywhatkit*

4. **wikipedia**: We'll use this to fetch a variety of information from the Wikipedia website. To install this module, type the below command in the terminal:
                                                                                                
                                                                                                *pip install Wikipedia*
                                                                                                
5. **pyaudio**: we’ll use this to recognize voice and acts as a microphone.
                                                                                            *pip install pyaudio.0.2.11 win-32*

## FEATURES OF JARVIS           

1. **Queries from the web**
Making queries is an essential part of one’s life, and nothing changes even for a developer working on Windows. We have addressed the essential part of a netizen’s life by enabling our voice assistant to search the web. Jarvis supports a plethora of search engines like Google, Bing and displays the result by scraping the searched queries.

2. **Accessing youtube videos**
Videos have remained as a main source of entertainment, one of the most prioritized tasks of virtual assistants. They are equally important for entertainment as well as educational purposes as most teaching and research activities in present times are done through Youtube. This helps in making the learning process more practical and out of the four walls of the classroom. 

3. **Time Remainder**
One of the main features of a voice assistant is to set a reminder for the user accordingly. Jarvis is no different when it comes to this. The user can set reminders to be notified about a task at a particular time. This will help users, especially developers to schedule their time and resources easily. All the user have to do is to input Set time to the assistant.

4. **Sending Emails**
Integrating mailing features to Jarvis eases the job of mailing, which otherwise would have to be done by opening the concerned email address. With Jarvis, you do not need to go for another tab to do one of the major task of your day to day affairs. The user can send emails to the desired receiver.

## CONTENT

**PROGRAM**

{
import pyttsx3 #pip install pyttsx3

import speech_recognition as sr #pip install speechRecognition

import datetime

import wikipedia #pip install wikipedia

import webbrowser

import os

import smtplib

engine = pyttsx3.init('sapi5')

voices = engine.getProperty('voices')

 print(voices[1].id)

engine.setProperty('voice', voices[0].id)

def speak(audio):

 engine.say(audio)

 engine.runAndWait()

def wishMe():

 hour = int(datetime.datetime.now().hour)

 if hour>=0 and hour<12:

 speak("Good Morning!")

 elif hour>=12 and hour<18:

 speak("Good Afternoon!") 

 else:

 speak("Good Evening!")

 speak("I am Jarvis Sir. Please tell me how may I help you")

def takeCommand():

 #It takes microphone input from the user and returns string output

 r = sr.Recognizer()

 with sr.Microphone() as source:

 print("Listening...")

 r.pause_threshold = 1

 audio = r.listen(source)

 try:

 print("Recognizing...")

 query = r.recognize_google(audio, language='en-in')

 print(f"User said: {query}\n")

 except Exception as e:

 print(e)

 print("Say that again please...")

 return "None"

 return query

def sendEmail(to, content):

 server = smtplib.SMTP('smtp.gmail.com', 587)

 server.ehlo()

 server.starttls()

 server.login('youremail@gmail.com', 'your-password')

 server.sendmail('youremail@gmail.com', to, content

 server.close()

if _name_ == "_main_":

 wishMe()

 while True:

  if 1:

 query = takeCommand().lower()

  Logic for executing tasks based on query

 if 'wikipedia' in query:

 speak('Searching Wikipedia...')

 query = query.replace("wikipedia", "")

 results = wikipedia.summary(query, sentences=2)

 speak("According to Wikipedia")

 print(results)

 speak(results)

 elif 'open youtube' in query:

 webbrowser.open("youtube.com")

 elif 'open google' in query:

 webbrowser.open("google.com")

 elif 'open stackoverflow' in query:

 webbrowser.open("stackoverflow.com")

 elif 'play music' in query:

 music_dir = 'D:\\Non Critical\\songs\\Favorite Songs2'

 songs = os.listdir(music_dir)

 print(songs)

 os.startfile(os.path.join(music_dir, songs[0]))

 elif 'the time' in query:

 strTime = datetime.datetime.now().strftime("%H:%M:%S")

 speak(f"Sir, the time is {strTime}")

 elif 'open code' in query:

 codePath = "C:\\Users\\Abhi\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"

 os.startfile(codePath)

 elif 'email to abhi' in query:

 try:

 speak("What should I say?")

 content = takeCommand()

 to = "abhiramramakoti@gmail.com"

 sendEmail(to, content)

 speak("Email has been sent!")
}

## REFFERENCES

1. VSCODE (online)
2. pyaudio (online)    https://www.lfd.uci.edu/~gohlke/pythonlibs/

## CONCLUSION

Through this voice assistant, we have automated various services using a single line command. It eases most of the tasks of the user like searching the TIME details, Google, youtube, related queries. We aim to make this project a complete server assistant and make it smart enough to act as a replacement for a general server administration. The future plans include integrating Jarvis with mobile using React Native to provide a synchronised experience between the two connected devices. Further, in the long run, Jarvis is planned to feature auto deployment supporting elastic beanstalk, backup files, and all operations which a general Server Administrator does. The functionality would be seamless enough to replace the Server Administrator with Jarvis.

