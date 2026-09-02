# Ex.no.8-Building-a-Simple-College-Admission-Chatbot
## Aim :
 To design, implement and test a simple rule-based chatbot in Python that answers frequently asked questions related to college admissions, such as courses offered, eligibility criteria, fees, application process, required documents, important dates, hostel facilities and contact details.
## OBJECTIVES
. To understand the basic working of a rule-based chatbot.. To create a keyword-based knowledge base for college
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
### Step 1: Import Required Libraries
●	re – Python's regular expression module, used to search for keyword patterns inside the user's message.
●	random – used to randomly pick one response when more than one reply is available for the same intent, so the chatbot does not sound repetitive.
<img width="605" height="37" alt="image" src="https://github.com/user-attachments/assets/5d19fe62-e644-4676-805b-2fe23826e1da" />
### Step 2: Design the Knowledge Base (Intents and Responses)
●	The knowledge base is stored as a Python dictionary, where every key is an intent (topic) such as courses, eligibility, fees or hostel.
●	Each intent stores a list of patterns (keywords/phrases likely to appear in a user's question) and a list of possible responses.
●	Organising the data this way makes the chatbot easy to extend — a new admission topic can be added simply by adding one more entry to the dictionary.
<img width="642" height="222" alt="image" src="https://github.com/user-attachments/assets/146afc71-fa16-4c84-a959-c91bbc2842eb" />
<img width="618" height="359" alt="image" src="https://github.com/user-attachments/assets/6b976de7-7dce-4418-a526-d25b31c66e79" />
Knowledge Base Summary
The table below summarises the complete knowledge base used by the chatbot:
<img width="669" height="403" alt="image" src="https://github.com/user-attachments/assets/991481a9-e6a3-4ce8-a3d0-2f07c4c7adf2" />
### Step 3: Function to Match User Input to an Intent
●	Converts the user's sentence to lower case so that matching is not case-sensitive.
●	re.search() scans the message for each pattern of every intent; the first intent whose pattern is found is returned.
●	If no pattern matches any intent, the function returns None so the fallback response can be used.
<img width="632" height="115" alt="image" src="https://github.com/user-attachments/assets/b4e8db5f-7e9c-4e48-9aeb-82d4c9e43097" />
### Step 4: Define the Chatbot Response Function
●	Calls match_intent() to identify what the user is asking about.
●	random.choice() picks one response from the matched intent's response list.
●	Returns a fallback message when the intent could not be identified, instead of leaving the user without a reply.
<img width="623" height="95" alt="image" src="https://github.com/user-attachments/assets/ab6895ac-bba4-4e66-9c51-cacf8d828286" />
### Step 5: Build the Interactive Conversation Loop
●	input() continuously reads the user's message from the console.
●	get_response() generates the reply for every message typed by the user.
●	The loop ends automatically once the matched intent is “goodbye” (e.g. the user types bye / exit / quit).
<img width="632" height="126" alt="image" src="https://github.com/user-attachments/assets/ae562d77-2461-4bed-b4c1-461b1cea5728" />
### Step 6: Test the Chatbot with Sample Queries
●	A list of realistic sample questions is used to automatically test every intent in the knowledge base.
●	Each query and the chatbot's corresponding reply are printed, which makes it easy to verify that every category of question is answered correctly.
<img width="622" height="113" alt="image" src="https://github.com/user-attachments/assets/4fdb6b4b-c684-4033-94e1-0d51fa19e99b" />
<img width="583" height="251" alt="image" src="https://github.com/user-attachments/assets/2ba37096-9575-4164-b4c3-ebca74ca9aab" />
### Step 7: Run the Chatbot
The complete script is executed in Python. Since input() cannot be used for automated testing, the sample_queries list from Step 6 is run first to validate every intent; the same get_response() function also powers the live chat() loop for real-time conversation with a user. The output produced on running the program is shown below.
Output
### Sample Conversation Output (Part 1)
●	The chatbot correctly greets the user and identifies the courses, eligibility, fees, application process and documents intents from the keywords present in each question.
<img width="646" height="470" alt="image" src="https://github.com/user-attachments/assets/016e1f31-dd01-4348-8815-70b3577b1391" />
### Sample Conversation Output (Part 2)
●	The remaining queries about dates, hostel facility and contact details are correctly matched to their respective intents.
●	The conversation ends gracefully with a goodbye message once the user types “Bye”, terminating the chat loop.
<img width="660" height="380" alt="image" src="https://github.com/user-attachments/assets/698ac90d-7962-406c-b381-03d16bedfb3b" />
## Conclusion
Thus, a simple rule-based College Admission Chatbot was successfully designed, implemented and tested using Python. The chatbot uses a keyword/pattern-based knowledge base to identify the intent behind a user's question and responds with an appropriate, pre-defined answer covering courses, eligibility, fees, application process, documents, dates, hostel and contact information. The experiment demonstrates the fundamental building blocks — knowledge base design, intent matching and response generation — on which more advanced NLP-based and AI-based chatbots are built.









