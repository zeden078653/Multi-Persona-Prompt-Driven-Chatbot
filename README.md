# **Project: Multi-Persona Prompt-Driven Chatbot**

**By: \[Mohammad Aman\]**

### **1\. How to Run This Project**

This web application is designed to be secure and run by anyone. To prevent exposing secret API keys, the application requires you to use your own Google Gemini API key.

1. **Get a Free API Key:** Visit [Google AI Studio](https://aistudio.google.com/app/apikey) and generate a free API key.  
2. **Enter the Key:** Copy your API key and paste it into the input field at the top of this application.  
3. **Start Chatting:** Once the key is entered, the chat input will become active, and you can begin your conversation\!

### **2\. Project Objective**

The goal of this project is to explore and demonstrate core prompt engineering principles through a feature-rich, interactive web application. The application is a web-based chatbot that can adopt various, distinct personas, but its functionality extends beyond simple chat. The primary focus is the design, testing, and refinement of the various prompts that guide the AI's behavior, personality, and specialized functions like summarization and reply generation.

This project directly showcases the ability to build reliable, context-aware, and human-like AI interactions while adhering to security best practices for API key management.

### **3\. Core Features**

* **Secure API Key Handling:** The app requires a user-provided API key, ensuring no secret keys are ever stored in the code or exposed in a public repository. The UI guides the user and only activates once a key is entered.  
* **Dynamic Persona Selection:** Users can choose from a list of predefined AI personas (e.g., Helpful Librarian, Sarcastic Teenager). The application dynamically loads a unique and detailed system prompt based on the user's selection to completely change the AI's conversational style.  
* **AI-Powered Conversation Summary:** With a single click, users can generate a concise, bullet-point summary of their entire conversation, demonstrating a practical, task-oriented use of the LLM.  
* **AI-Powered Reply Suggestions:** After the AI responds, the application uses another LLM call to generate three context-aware reply suggestions for the user, showcasing the ability to use AI to facilitate smoother and faster interactions.  
* **Contextual Memory:** The AI remembers the chat history within a session to hold a coherent, multi-turn conversation that respects the established context.  
* **Responsive UI:** The interface is clean, responsive, and provides clear feedback to the user, including loading indicators and disabled states.

### **4\. Prompt Engineering Methodology**

My approach to designing the prompts for each feature followed a structured, iterative methodology.

#### **a. Persona System Prompts**

For each persona, I defined a clear set of attributes and translated them into a detailed system prompt.

* **Role-Playing:** The prompt starts with a clear directive like "You are..." to establish the persona.  
* **Rule Definition:** I used bullet points to lay out clear, actionable rules for the AI's tone, vocabulary, and constraints.  
* **Few-Shot Prompting:** For complex personas like the Shakespearean Poet, I included examples of user questions and ideal AI responses. This provides the model with a concrete pattern to follow, significantly improving output consistency.

#### **b. Functional Prompts**

For features like suggestions and summaries, a different prompting strategy was required:

* **Summarization Prompt:** The prompt takes the entire chat history as context and gives a clear, one-shot command: "Provide a concise, bullet-point summary of the key topics discussed in the following conversation..."  
* **Suggestion Prompt:** This prompt is more nuanced. It considers the AI's last message and the current persona to generate relevant replies. Crucially, it instructs the model to return its output in a specific format: "Provide ONLY a valid JSON array of strings." This ensures the response can be reliably parsed and used by the application, demonstrating an understanding of how to get structured data from an LLM.

#### **c. Iteration and Refinement**

Initial testing revealed areas for improvement. For example, the first version of the "Sarcastic Teenager" was often unhelpfully rude.

* **Problem:** The AI refused to answer questions, violating the core function of the chatbot.  
* **Analysis:** The prompt over-emphasized the negative trait (sarcasm) without a balancing instruction.  
* **Solution:** I iterated on the prompt to add a new rule: "Your primary goal is still to provide a correct answer, but do so begrudgingly and with heavy sarcasm." This refinement produced a character that was both in-character and functional. This process of testing, analyzing, and refining was applied to all personas and features.

### **5\. Technical Implementation**

* **Frontend:** HTML, Tailwind CSS, JavaScript  
* **AI Model API:** Google Gemini (gemini-2.0-flash)  
* **Security:** API keys are handled entirely on the client-side via an input field and are never stored in the repository, protecting them from exposure. The application logic is built to handle potential API errors gracefully.

### **6\. Conclusion & Future Work**

This project successfully demonstrates a practical understanding of prompt engineering, from controlling an AI's personality to using it for specific, structured tasks. It also highlights an awareness of security best practices in a real-world application.

**Potential next steps could include:**

* **Testing Across Models:** Integrating APIs from Claude or Mistral to compare how different models interpret the same prompt.  
* **Storing Chat History:** Using localStorage to save a conversation so it persists even after the browser is refreshed.  
* **Expanding Personas:** Adding more complex personas that might require more advanced techniques like prompt chaining to accomplish multi-step tasks.