import wikipediaapi

# Specify a user agent string
user_agent = "MyWikiBot/1.0 (https://github.com/yourusername/yourrepository)"

# Initialize Wikipedia object with the specified user agent
wiki = wikipediaapi.Wikipedia('en', user_agent=user_agent)

import wikipediaapi
import psutil
import pyttsx3

# Initialize Wikipedia API
wiki = wikipediaapi.Wikipedia('en')

# Initialize Text-to-Speech Engine
engine = pyttsx3.init()

# Define a function to answer user's questions
def answer_question(question):
    page = wiki.page(question)
    if page.exists():
        summary = page.summary
        print(summary)
        engine.say(summary)
        engine.runAndWait()
    else:
        print("Sorry, I couldn't find information on that topic.")

# Define a function to check PC's CPU usage
def check_cpu_usage():
    cpu_usage = psutil.cpu_percent()
    print(f"Current CPU usage: {cpu_usage}%")
    if cpu_usage > 80:
        print("High CPU usage detected! Please close some applications.")

# Main loop
while True:
    user_input = input("How can I help you? ")
    if user_input.lower() == "exit":
        break
    elif "doubt" in user_input.lower() or "question" in user_input.lower():
        question = input("What's your question? ")
        answer_question(question)
    elif "cpu" in user_input.lower() or "usage" in user_input.lower():
        check_cpu_usage()
    else:
        print("Sorry, I didn't understand that.")
