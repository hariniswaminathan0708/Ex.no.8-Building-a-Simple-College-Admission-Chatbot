# Ex.no.8-Building-a-Simple-College-Admission-Chatbot
## Aim 
To design, implement and test a simple rule-based chatbot in Python that answers frequently asked questions related to college admissions, such as courses offered, eligibility criteria, fees, application process, required documents, important dates, hostel facilities and contact details.
## OBJECTIVES
To understand the basic working of a rule-based chatbot.. To create a keyword-based knowledge base for college
admission queries.. To implement intent matching using Python regular expressions.. To test the chatbot using
different sample queries.
### Introduction
A chatbot is a software application that simulates a conversation with a human user, typically through text. A rule-based (or pattern-matching) chatbot works by comparing the user's message against a predefined set of keywords or patterns and returning a suitable pre-written response. It does not require large training datasets or heavy computation, which makes it an easy and beginner-friendly starting point for understanding how conversational AI systems are built. In this experiment, a College Admission Chatbot is developed to act as a virtual help-desk assistant that instantly answers common queries asked by prospective students.
## ALGORITHM
1.Start the program. 2.Import the required Python libraries. 3.Create the chatbot knowledge base with intents, patterns
and responses. 4.Accept the user's input. 5.Convert the input into lowercase. 6.Match the input with predefined
patterns using regular expressions. 7.Identify the corresponding intent. 8.Select and display a suitable response. 9.lf no
intent matches, display a fallback response. 10.Continue the conversation until the user enters a goodbye command.
11.Stop the program.
### Procedure
```
Step 1: Import Required Libraries
re – Python's regular expression module, used to search for keyword patterns inside the user's message.
random – used to randomly select one response when more than one response is available.

Step 2: Design the Knowledge Base
The knowledge base is stored as a Python dictionary.
Each key represents an intent/topic, such as:
Courses
Eligibility
Fees
Dates
Application process
Documents
Hostel
Contact
Each intent contains:
Patterns – keywords or phrases likely to appear in the user's question.
Responses – possible answers given by the chatbot.
This structure makes the chatbot easy to extend by adding new intents.

Step 3: Function to Match User Input to an Intent
The user's sentence is converted to lowercase so that matching is case-insensitive.
re.search() checks the user's message against the patterns of every intent.
If a matching pattern is found, the corresponding intent is returned.
If no pattern matches, the function returns None.

Step 4: Define the Chatbot Response Function
get_response() calls match_intent() to identify the user's query.
If an intent is identified, random.choice() selects a response from the corresponding response list.
If no intent is identified, a fallback response is returned.
This ensures that the chatbot always provides a reply.

Step 5: Build the Interactive Conversation Loop
input() continuously reads messages from the user.
get_response() generates a suitable reply for every message.
The chatbot prints the response on the screen.
The loop terminates when the user enters a goodbye-related word such as:
bye
exit
quit

Step 6: Test the Chatbot with Sample Queries
A list of realistic sample questions is created.
The questions cover all the intents in the knowledge base.
Each question is passed to get_response().
The question and corresponding chatbot response are displayed.
This helps verify that all categories are working correctly.

Step 7: Run the Chatbot
The complete Python program is executed.
The sample queries are tested first.
The chat() function then starts the interactive conversation.
The user can type questions related to admission.
The chatbot identifies the intent and provides the appropriate predefined response.
The conversation ends when the user types Bye, Exit, or Quit.
```
## PROGRAM
```
import re
import random

knowledge_base = {
    "greeting": {
        "patterns": [
            r"\bhi\b",
            r"\bhello\b",
            r"\bhey\b",
            r"\bgood morning\b",
            r"\bgood afternoon\b"
        ],
        "responses": [
            "Hello! Welcome to the College Admission Help Desk. "
            "How can I assist you today?"
        ]
    },

    "courses": {
        "patterns": [
            r"\bcourse\b",
            r"\bprogram\b",
            r"\bbranch\b",
            r"\bdepartment\b",
            r"\bspecialization\b"
        ],
        "responses": [
            "We offer B.Tech programs in Information Technology, "
            "Computer Science, ECE, EEE and Mechanical Engineering, "
            "along with M.Tech and MBA programs."
        ]
    },

    "eligibility": {
        "patterns": [
            r"\beligibility\b",
            r"\bqualification\b",
            r"\bcriteria\b",
            r"\bcutoff\b"
        ],
        "responses": [
            "For B.Tech, candidates must have completed 10+2 with "
            "Physics, Chemistry and Mathematics, securing at least "
            "60% aggregate marks."
        ]
    },

    "fees": {
        "patterns": [
            r"\bfee\b",
            r"\btuition\b",
            r"\bcost\b",
            r"\bscholarship\b"
        ],
        "responses": [
            "The annual tuition fee for B.Tech programs is approximately "
            "Rs. 85,000. Merit and government scholarships are also "
            "available for eligible students."
        ]
    },

    "dates": {
        "patterns": [
            r"\blast date\b",
            r"\bdeadline\b",
            r"\bschedule\b",
            r"\bdate\b"
        ],
        "responses": [
            "Admissions begin on 1st June and the last date to apply "
            "is 31st July."
        ]
    },

    "application_process": {
        "patterns": [
            r"\bapply\b",
            r"\bapplication\b",
            r"\bregister\b",
            r"\bhow to join\b"
        ],
        "responses": [
            "Apply online through the college admission portal by "
            "filling the application form, uploading documents, and "
            "paying the registration fee."
        ]
    },

    "documents": {
        "patterns": [
            r"\bdocument\b",
            r"\bcertificate\b",
            r"\bmarksheet\b"
        ],
        "responses": [
            "Please keep the following documents ready: 10th and 12th "
            "mark sheets, transfer certificate, community certificate, "
            "passport size photographs and Aadhaar card."
        ]
    },

    "hostel": {
        "patterns": [
            r"\bhostel\b",
            r"\baccommodation\b",
            r"\broom facility\b"
        ],
        "responses": [
            "Separate hostel facilities are available for boys and "
            "girls with mess, Wi-Fi and 24x7 security on campus."
        ]
    },

    "contact": {
        "patterns": [
            r"\bcontact\b",
            r"\bphone\b",
            r"\bemail\b",
            r"\baddress\b"
        ],
        "responses": [
            "You can reach the admission office at "
            "admissions@college.edu.in or call +91-9876543210 "
            "between 9 AM and 5 PM."
        ]
    },

    "thanks / goodbye": {
        "patterns": [
            r"\bthank\b",
            r"\bbye\b",
            r"\bsee you\b",
            r"\bexit\b",
            r"\bquit\b"
        ],
        "responses": [
            "Thank you for visiting the College Admission Help Desk. "
            "Wishing you all the best!"
        ]
    }
}


fallback_responses = [
    "I'm sorry, I did not quite understand that. "
    "Could you please rephrase your question?",

    "I can help with courses, eligibility, fees, application "
    "process, documents, dates, hostel and contact details."
]


def match_intent(user_input):
    user_input = user_input.lower()

    for intent, data in knowledge_base.items():
        for pattern in data["patterns"]:
            if re.search(pattern, user_input):
                return intent

    return None

def get_response(user_input):
    intent = match_intent(user_input)

    if intent:
        return random.choice(knowledge_base[intent]["responses"])

    return random.choice(fallback_responses)


def chat():
    print("College Admission Chatbot")
    print("=" * 55)

    while True:
        user_input = input("You: ")
        response = get_response(user_input)

        print("Bot:", response)

        if match_intent(user_input) == "thanks / goodbye":
            break


sample_queries = [
    "Hi there",
    "What courses do you offer?",
    "What is the eligibility criteria for B.Tech?",
    "How much is the tuition fee?",
    "How can I apply for admission?",
    "What documents are required?",
    "When is the last date to apply?",
    "Do you provide hostel facility?",
    "What is your contact number?",
    "Thank you for the help",
    "Bye"
]

print("College Admission Chatbot")
print("=" * 55)

for query in sample_queries:
    print("You:", query)
    print("Bot:", get_response(query))
    print("-" * 55)

chat()
```

## OUTPUT
<img width="1525" height="682" alt="Screenshot 2026-09-22 223534" src="https://github.com/user-attachments/assets/f22c543f-e6eb-4054-8802-d61ca2cfc642" />
<img width="858" height="170" alt="Screenshot 2026-09-22 223550" src="https://github.com/user-attachments/assets/cf753ec6-7675-4406-b472-0b51e57f7ea9" />

## Conclusion
Thus, a simple rule-based College Admission Chatbot was successfully designed, implemented and tested using Python. The chatbot uses a keyword/pattern-based knowledge base to identify the intent behind a user's question and responds with an appropriate, pre-defined answer covering courses, eligibility, fees, application process, documents, dates, hostel and contact information. The experiment demonstrates the fundamental building blocks — knowledge base design, intent matching and response generation — on which more advanced NLP-based and AI-based chatbots are built.









