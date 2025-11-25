# Build-a-Chatbot-using-if-else
# Create a simple rule-based chatbot using if-elif-else

chatbot_code_basic = """#!/usr/bin/env python3
\"\"\"
Simple Rule-Based Chatbot
Author: Python Learning Example
Date: November 2025

Description:
This is a basic rule-based chatbot that uses if-elif-else statements
to respond to user inputs. The chatbot can handle greetings, questions,
and basic conversation.
\"\"\"

def chatbot():
    \"\"\"
    Main chatbot function that handles user interaction through
    input/output loop and conditional statements.
    \"\"\"
    
    print("=" * 60)
    print("Welcome to SimpleBot!")
    print("=" * 60)
    print("I'm a simple rule-based chatbot. I can chat with you!")
    print("Type 'bye', 'quit', or 'exit' to end the conversation.")
    print("-" * 60)
    
    # Main conversation loop - continues until user exits
    while True:
        # Get user input and convert to lowercase for easier matching
        user_input = input("\\nYou: ").strip().lower()
        
        # Exit conditions - check if user wants to end conversation
        if user_input in ['bye', 'goodbye', 'quit', 'exit']:
            print("Bot: Goodbye! Have a great day! 👋")
            break
        
        # Empty input handling
        elif user_input == '':
            print("Bot: Please say something! I'm here to chat.")
        
        # Greetings
        elif user_input in ['hi', 'hello', 'hey', 'greetings']:
            print("Bot: Hello! How can I help you today? 😊")
        
        # How are you questions
        elif 'how are you' in user_input:
            print("Bot: I'm doing great! Thanks for asking. How about you?")
        
        # Bot identity questions
        elif 'your name' in user_input or 'who are you' in user_input:
            print("Bot: I'm SimpleBot, a rule-based chatbot created to assist you!")
        
        # Age questions
        elif 'how old' in user_input or 'your age' in user_input:
            print("Bot: I'm ageless! I was created recently, but age doesn't apply to bots.")
        
        # Help requests
        elif 'help' in user_input:
            print("Bot: I can chat with you about various topics!")
            print("     Try asking me about:")
            print("     - Greetings (hello, hi)")
            print("     - My identity (who are you, what's your name)")
            print("     - Time or weather")
            print("     - Or just chat casually!")
        
        # Weather questions
        elif 'weather' in user_input:
            print("Bot: I don't have access to real-time weather data,")
            print("     but I hope it's nice wherever you are! ☀️")
        
        # Time questions
        elif 'time' in user_input:
            import datetime
            current_time = datetime.datetime.now().strftime("%H:%M:%S")
            print(f"Bot: The current time is {current_time}. ⏰")
        
        # Thank you responses
        elif 'thank' in user_input:
            print("Bot: You're welcome! Happy to help! 😊")
        
        # Jokes
        elif 'joke' in user_input:
            print("Bot: Why do programmers prefer dark mode?")
            print("     Because light attracts bugs! 🐛😄")
        
        # Capabilities questions
        elif 'what can you do' in user_input or 'your capabilities' in user_input:
            print("Bot: I can:")
            print("     1. Answer basic questions")
            print("     2. Have simple conversations")
            print("     3. Tell you the time")
            print("     4. Tell jokes")
            print("     5. Provide information about myself")
        
        # Default response for unrecognized input
        else:
            print("Bot: I'm not sure I understand that.")
            print("     Could you rephrase or type 'help' for options?")


# Main execution
if __name__ == "__main__":
    chatbot()
"""

print("=" * 80)
print("BASIC RULE-BASED CHATBOT CODE")
print("=" * 80)
print(chatbot_code_basic)

# Save to file
with open('chatbot_basic.py', 'w') as f:
    f.write(chatbot_code_basic)

print("\n✓ Basic chatbot saved to 'chatbot_basic.py'")
# Create an advanced chatbot with more features

chatbot_advanced = """#!/usr/bin/env python3
\"\"\"
Advanced Rule-Based Chatbot with Multiple Features
Author: Python Learning Example
Date: November 2025

Description:
An enhanced rule-based chatbot with conversation history tracking,
randomized responses, and multiple conversation domains.
\"\"\"

import random
import datetime


class AdvancedChatbot:
    \"\"\"
    Advanced chatbot class with conversation history and
    multiple response options.
    \"\"\"
    
    def __init__(self, bot_name="AdvancedBot"):
        \"\"\"Initialize the chatbot with name and conversation history.\"\"\"
        self.bot_name = bot_name
        self.conversation_history = []
        self.user_name = None
        
        # Response dictionaries for varied responses
        self.greetings = [
            "Hello! How can I assist you today?",
            "Hi there! What can I do for you?",
            "Hey! Great to see you!",
            "Greetings! How may I help you?"
        ]
        
        self.goodbyes = [
            "Goodbye! Take care!",
            "See you later! Have a great day!",
            "Bye! Come back anytime!",
            "Farewell! It was nice chatting with you!"
        ]
        
        self.thanks_responses = [
            "You're welcome! Happy to help!",
            "No problem at all!",
            "Glad I could assist you!",
            "Anytime! That's what I'm here for!"
        ]
        
        # Domain-specific knowledge
        self.programming_topics = {
            'python': "Python is a versatile programming language known for its simplicity and readability!",
            'javascript': "JavaScript powers the web! It's essential for frontend development.",
            'java': "Java is a robust, object-oriented language used in enterprise applications.",
            'c++': "C++ is powerful for system programming and game development!",
            'sql': "SQL is the standard language for database management and queries."
        }
        
        self.jokes = [
            ("Why do programmers prefer dark mode?", "Because light attracts bugs! 🐛"),
            ("Why was the JavaScript developer sad?", "Because he didn't Node how to Express himself! 😄"),
            ("What's a programmer's favorite hangout place?", "The Foo Bar! 🍺"),
            ("Why do Python programmers wear glasses?", "Because they can't C! 👓"),
            ("How many programmers does it take to change a light bulb?", "None. It's a hardware problem! 💡")
        ]
    
    def add_to_history(self, user_input, bot_response):
        \"\"\"Store conversation in history.\"\"\"
        timestamp = datetime.datetime.now().strftime("%H:%M:%S")
        self.conversation_history.append({
            'time': timestamp,
            'user': user_input,
            'bot': bot_response
        })
    
    def show_history(self):
        \"\"\"Display conversation history.\"\"\"
        if not self.conversation_history:
            return "No conversation history yet!"
        
        history_text = "\\n📜 Conversation History:\\n" + "=" * 50
        for entry in self.conversation_history[-5:]:  # Show last 5 exchanges
            history_text += f"\\n[{entry['time']}]"
            history_text += f"\\n  You: {entry['user']}"
            history_text += f"\\n  Bot: {entry['bot']}"
        return history_text
    
    def get_response(self, user_input):
        \"\"\"
        Generate appropriate response based on user input
        using if-elif-else conditional logic.
        \"\"\"
        
        # Convert to lowercase for easier matching
        user_input_lower = user_input.strip().lower()
        response = ""
        
        # Exit conditions
        if user_input_lower in ['bye', 'goodbye', 'quit', 'exit', 'see you']:
            response = random.choice(self.goodbyes)
            if self.user_name:
                response = f"{response} {self.user_name}! 👋"
        
        # Empty input
        elif user_input_lower == '':
            response = "Please say something! I'm listening. 👂"
        
        # Name introduction
        elif 'my name is' in user_input_lower:
            # Extract name after "my name is"
            name_parts = user_input_lower.split('my name is')
            if len(name_parts) > 1:
                self.user_name = name_parts[1].strip().title()
                response = f"Nice to meet you, {self.user_name}! 😊"
        
        # Greetings
        elif user_input_lower in ['hi', 'hello', 'hey', 'greetings', 'howdy']:
            response = random.choice(self.greetings)
            if self.user_name:
                response = response.replace('!', f', {self.user_name}!')
        
        # How are you
        elif 'how are you' in user_input_lower:
            response = "I'm functioning perfectly! Thanks for asking. How about you?"
        
        # Bot identity
        elif 'your name' in user_input_lower or 'who are you' in user_input_lower:
            response = f"I'm {self.bot_name}, your friendly rule-based chatbot assistant!"
        
        # Help command
        elif user_input_lower == 'help':
            response = \"\"\"🆘 Available Commands:
            
1. Greetings: Say 'hello', 'hi', 'hey'
2. Identity: Ask 'what is your name' or 'who are you'
3. Time: Ask 'what time is it'
4. Date: Ask 'what's the date'
5. Math: Ask 'calculate [expression]' (e.g., 'calculate 5 + 3')
6. Programming: Ask about python, java, javascript, c++, sql
7. Jokes: Type 'joke' or 'tell me a joke'
8. History: Type 'history' to see conversation history
9. Exit: Type 'bye', 'quit', or 'exit' to end chat
\"\"\"
        
        # Time query
        elif 'time' in user_input_lower and 'what' in user_input_lower:
            current_time = datetime.datetime.now().strftime("%I:%M %p")
            response = f"The current time is {current_time}. ⏰"
        
        # Date query
        elif 'date' in user_input_lower and 'what' in user_input_lower:
            current_date = datetime.datetime.now().strftime("%B %d, %Y")
            response = f"Today's date is {current_date}. 📅"
        
        # Day of week
        elif 'day' in user_input_lower and 'what' in user_input_lower:
            day = datetime.datetime.now().strftime("%A")
            response = f"Today is {day}!"
        
        # Math calculations
        elif 'calculate' in user_input_lower or 'solve' in user_input_lower:
            try:
                # Extract expression after 'calculate' or 'solve'
                expression = user_input_lower.split('calculate')[-1].split('solve')[-1].strip()
                # Safely evaluate mathematical expression
                result = eval(expression, {"__builtins__": {}}, {})
                response = f"The answer is: {result} 🧮"
            except:
                response = "I couldn't calculate that. Please use format: 'calculate 5 + 3'"
        
        # Programming language queries
        elif any(lang in user_input_lower for lang in self.programming_topics.keys()):
            for lang, info in self.programming_topics.items():
                if lang in user_input_lower:
                    response = info
                    break
        
        # Jokes
        elif 'joke' in user_input_lower:
            joke_setup, joke_punchline = random.choice(self.jokes)
            response = f"{joke_setup}\\n     {joke_punchline}"
        
        # Conversation history
        elif 'history' in user_input_lower:
            response = self.show_history()
        
        # Thank you
        elif 'thank' in user_input_lower:
            response = random.choice(self.thanks_responses)
        
        # Capabilities
        elif 'what can you do' in user_input_lower or 'capabilities' in user_input_lower:
            response = \"\"\"I can do many things! 🤖
            
✅ Answer questions about programming languages
✅ Perform basic calculations
✅ Tell you the time and date
✅ Tell jokes to brighten your day
✅ Keep track of our conversation history
✅ Have casual conversations
            
Type 'help' for detailed commands!\"\"\"
        
        # Weather (limitation acknowledgment)
        elif 'weather' in user_input_lower:
            response = "I don't have access to real-time weather data, but I hope it's pleasant! ⛅"
        
        # Age question
        elif 'how old' in user_input_lower or 'age' in user_input_lower:
            response = "I'm timeless! Created in 2025, but age is just a number for bots. 🤖"
        
        # Compliments
        elif any(word in user_input_lower for word in ['good', 'great', 'awesome', 'excellent']):
            response = "Thank you! I appreciate your kind words! 😊"
        
        # Default fallback
        else:
            response = \"\"\"I'm not sure I understand that. 🤔
            
Try asking me about:
- Programming languages (Python, Java, JavaScript, etc.)
- Time or date
- Calculations (e.g., 'calculate 10 * 5')
- Or type 'help' for all available commands!\"\"\"
        
        # Add to conversation history
        self.add_to_history(user_input, response)
        
        return response
    
    def run(self):
        \"\"\"Main chatbot loop.\"\"\"
        print("=" * 70)
        print(f"    Welcome to {self.bot_name}!")
        print("=" * 70)
        print("I'm an advanced rule-based chatbot with multiple capabilities!")
        print("Type 'help' to see what I can do, or 'bye' to exit.")
        print("-" * 70)
        
        while True:
            try:
                user_input = input("\\nYou: ").strip()
                
                if not user_input:
                    continue
                
                response = self.get_response(user_input)
                print(f"Bot: {response}")
                
                # Check if user wants to exit
                if user_input.lower() in ['bye', 'goodbye', 'quit', 'exit']:
                    break
                    
            except KeyboardInterrupt:
                print("\\n\\nBot: Interrupted! Goodbye! 👋")
                break
            except Exception as e:
                print(f"Bot: Oops! An error occurred: {e}")


# Main execution
if __name__ == "__main__":
    bot = AdvancedChatbot("SmartBot")
    bot.run()
"""

print("=" * 80)
print("ADVANCED RULE-BASED CHATBOT CODE")
print("=" * 80)
print(chatbot_advanced)

# Save to file
with open('chatbot_advanced.py', 'w') as f:
    f.write(chatbot_advanced)

print("\n✓ Advanced chatbot saved to 'chatbot_advanced.py'")
# Create comprehensive documentation

documentation = """# RULE-BASED CHATBOT IMPLEMENTATION GUIDE

## Overview

A rule-based chatbot uses predefined patterns and if-elif-else conditional logic
to respond to user inputs. Unlike AI-powered chatbots, rule-based bots follow
explicit rules defined by the developer.

---

## Core Concepts

### 1. Input/Output Loop

The chatbot continuously accepts user input and provides responses until
an exit condition is met:

```python
while True:
    user_input = input("You: ")
    if exit_condition:
        break
    # Process and respond
```

### 2. If-Elif-Else Logic

Conditional statements determine appropriate responses based on input patterns:

```python
if 'hello' in user_input:
    print("Hi there!")
elif 'bye' in user_input:
    print("Goodbye!")
else:
    print("I don't understand.")
```

### 3. Input Normalization

Convert input to lowercase and strip whitespace for consistent matching:

```python
user_input = input("You: ").strip().lower()
```

---

## Basic Chatbot Structure

### Minimal Implementation

```python
def chatbot():
    print("Welcome to SimpleBot!")
    
    while True:
        user_input = input("You: ").strip().lower()
        
        # Exit condition
        if user_input in ['bye', 'quit', 'exit']:
            print("Bot: Goodbye!")
            break
        
        # Greetings
        elif user_input in ['hi', 'hello']:
            print("Bot: Hello! How can I help?")
        
        # Help
        elif user_input == 'help':
            print("Bot: I can chat with you!")
        
        # Default fallback
        else:
            print("Bot: I don't understand.")

if __name__ == "__main__":
    chatbot()
```

---

## Key Features to Implement

### 1. Multiple Exit Conditions

```python
if user_input in ['bye', 'goodbye', 'quit', 'exit', 'see you']:
    print("Bot: Goodbye!")
    break
```

### 2. Keyword Matching with 'in' Operator

```python
elif 'weather' in user_input:
    print("Bot: I don't have weather data.")

elif 'your name' in user_input:
    print("Bot: I'm a chatbot!")
```

### 3. Multiple Condition Checking

```python
elif 'your name' in user_input or 'who are you' in user_input:
    print("Bot: I'm SimpleBot!")
```

### 4. Empty Input Handling

```python
elif user_input == '':
    print("Bot: Please say something!")
```

---

## Advanced Features

### 1. Random Responses

```python
import random

greetings = ["Hello!", "Hi there!", "Hey!", "Greetings!"]

if user_input in ['hi', 'hello']:
    print("Bot:", random.choice(greetings))
```

### 2. Time/Date Integration

```python
import datetime

if 'time' in user_input:
    current_time = datetime.datetime.now().strftime("%H:%M:%S")
    print(f"Bot: The time is {current_time}")

if 'date' in user_input:
    current_date = datetime.datetime.now().strftime("%B %d, %Y")
    print(f"Bot: Today is {current_date}")
```

### 3. Basic Calculations

```python
if 'calculate' in user_input:
    try:
        expression = user_input.split('calculate')[1].strip()
        result = eval(expression, {"__builtins__": {}}, {})
        print(f"Bot: The answer is {result}")
    except:
        print("Bot: Couldn't calculate that.")
```

### 4. Conversation History

```python
conversation_history = []

def add_to_history(user_msg, bot_msg):
    conversation_history.append({
        'user': user_msg,
        'bot': bot_msg
    })

if 'history' in user_input:
    for entry in conversation_history[-5:]:
        print(f"You: {entry['user']}")
        print(f"Bot: {entry['bot']}")
```

### 5. Name Recognition

```python
user_name = None

if 'my name is' in user_input:
    name_parts = user_input.split('my name is')
    user_name = name_parts[1].strip().title()
    print(f"Bot: Nice to meet you, {user_name}!")
```

---

## Class-Based Implementation

### Advantages of Object-Oriented Approach

- **Encapsulation**: Keep data and methods together
- **State Management**: Track conversation state
- **Reusability**: Create multiple bot instances
- **Maintainability**: Easier to modify and extend

### Basic Class Structure

```python
class Chatbot:
    def __init__(self, name):
        self.name = name
        self.history = []
    
    def get_response(self, user_input):
        # Process input and return response
        pass
    
    def run(self):
        # Main conversation loop
        while True:
            user_input = input("You: ")
            response = self.get_response(user_input)
            print(f"Bot: {response}")
            
            if user_input.lower() in ['bye', 'quit']:
                break

bot = Chatbot("MyBot")
bot.run()
```

---

## Best Practices

### 1. Code Organization

- Keep related conditions together
- Use functions for repeated logic
- Add comments explaining complex conditions
- Use meaningful variable names

### 2. User Experience

- Provide clear welcome message
- Explain how to exit the chat
- Offer help command
- Give friendly fallback responses

### 3. Input Handling

- Always normalize input (lowercase, strip)
- Handle empty inputs gracefully
- Consider typos and variations
- Use flexible keyword matching

### 4. Response Quality

- Vary responses to avoid repetition
- Be conversational and friendly
- Acknowledge limitations honestly
- Provide helpful suggestions

### 5. Error Handling

```python
try:
    # Risky operation
    result = some_operation()
except Exception as e:
    print(f"Bot: An error occurred: {e}")
```

---

## Common Patterns

### Pattern 1: Multi-Word Keyword Matching

```python
if 'how are you' in user_input:
    print("Bot: I'm great!")
```

### Pattern 2: Multiple Keywords (OR logic)

```python
if any(word in user_input for word in ['thank', 'thanks']):
    print("Bot: You're welcome!")
```

### Pattern 3: Multiple Keywords (AND logic)

```python
if 'weather' in user_input and 'tomorrow' in user_input:
    print("Bot: I don't have future weather data.")
```

### Pattern 4: Exact Match vs Partial Match

```python
# Exact match
if user_input == 'help':
    print("Bot: Help menu...")

# Partial match
elif 'help' in user_input:
    print("Bot: Need assistance?")
```

---

## Testing Your Chatbot

### Test Cases

1. **Basic greetings**: "hi", "hello", "hey"
2. **Exit commands**: "bye", "quit", "exit"
3. **Empty input**: Just press Enter
4. **Unknown input**: Random text
5. **Case variations**: "HELLO", "HeLLo"
6. **Multiple keywords**: "hello how are you"

### Sample Test Session

```
You: hello
Bot: Hi there! How can I help?

You: what's your name
Bot: I'm SimpleBot!

You: what time is it
Bot: The current time is 19:30:00

You: tell me a joke
Bot: Why do programmers prefer dark mode? Because light attracts bugs!

You: bye
Bot: Goodbye!
```

---

## Limitations of Rule-Based Chatbots

1. **Fixed Responses**: Can only respond to predefined patterns
2. **No Learning**: Cannot improve from conversations
3. **Context Limited**: Doesn't understand conversation flow deeply
4. **Maintenance**: Requires manual updates for new patterns
5. **Scalability**: Becomes complex with many rules

---

## Enhancement Ideas

### 1. Add Domain-Specific Knowledge

```python
knowledge_base = {
    'python': 'Python is a high-level programming language...',
    'java': 'Java is an object-oriented language...',
}

for topic, info in knowledge_base.items():
    if topic in user_input:
        print(f"Bot: {info}")
```

### 2. Multi-Turn Conversations

```python
bot_state = {'asking_for': None}

if bot_state['asking_for'] == 'name':
    user_name = user_input
    print(f"Bot: Nice to meet you, {user_name}!")
    bot_state['asking_for'] = None
```

### 3. Regular Expressions

```python
import re

# Match phone numbers
if re.search(r'\\d{3}-\\d{3}-\\d{4}', user_input):
    print("Bot: I see a phone number!")
```

### 4. Sentiment Detection

```python
positive_words = ['good', 'great', 'awesome', 'excellent']
negative_words = ['bad', 'terrible', 'awful', 'horrible']

if any(word in user_input for word in positive_words):
    print("Bot: Glad to hear that!")
elif any(word in user_input for word in negative_words):
    print("Bot: I'm sorry to hear that.")
```

---

## Running Your Chatbot

### Method 1: Command Line

```bash
python chatbot.py
```

### Method 2: Python Interpreter

```python
>>> from chatbot import Chatbot
>>> bot = Chatbot("MyBot")
>>> bot.run()
```

### Method 3: Jupyter Notebook

```python
%run chatbot.py
```

---

## Debugging Tips

### 1. Print Statements

```python
print(f"DEBUG: user_input = '{user_input}'")
print(f"DEBUG: Condition matched = {condition}")
```

### 2. Log Conversations

```python
with open('chat_log.txt', 'a') as f:
    f.write(f"User: {user_input}\\n")
    f.write(f"Bot: {response}\\n")
```

### 3. Test Individual Conditions

```python
test_input = "hello how are you"
if 'hello' in test_input:
    print("PASS: Greeting detected")
```

---

## Sample Execution Flow

```
1. Program starts
2. Display welcome message
3. Enter while loop
4. Get user input
5. Check if exit condition → if yes, break loop
6. Check if greeting → respond with greeting
7. Check if question → provide answer
8. If no match → default response
9. Print bot response
10. Loop back to step 4
11. Display goodbye message
12. Program ends
```

---

## Conclusion

Rule-based chatbots are excellent learning projects that teach:
- Conditional logic (if-elif-else)
- Input/output operations
- String manipulation
- Loop control
- Function design
- User experience considerations

While limited compared to AI chatbots, they are simple, transparent,
and perfect for specific use cases where predictable behavior is desired.
"""

print(documentation)

# Save documentation
with open('chatbot_guide.txt', 'w') as f:
    f.write(documentation)

print("\n✓ Comprehensive guide saved to 'chatbot_guide.txt'")
import plotly.graph_objects as go

# Create figure
fig = go.Figure()

# Define node positions and properties
# Ovals for Start/End
# Rectangles for processes
# Diamond for decision

nodes = {
    'start': {'x': 0.5, 'y': 1.0, 'text': 'Start', 'shape': 'oval'},
    'welcome': {'x': 0.5, 'y': 0.9, 'text': 'Display welcome<br>message', 'shape': 'rect'},
    'loop': {'x': 0.5, 'y': 0.78, 'text': 'Input Loop<br>(while True)', 'shape': 'rect'},
    'input': {'x': 0.5, 'y': 0.66, 'text': 'Get user input', 'shape': 'rect'},
    'exit_check': {'x': 0.5, 'y': 0.52, 'text': 'Exit command?', 'shape': 'diamond'},
    'goodbye': {'x': 0.75, 'y': 0.38, 'text': 'Display goodbye', 'shape': 'rect'},
    'end': {'x': 0.75, 'y': 0.26, 'text': 'Exit', 'shape': 'oval'},
    'check': {'x': 0.25, 'y': 0.38, 'text': 'Check conditions<br>(if-elif-else)', 'shape': 'rect'},
    'generate': {'x': 0.25, 'y': 0.26, 'text': 'Generate response', 'shape': 'rect'},
    'display': {'x': 0.25, 'y': 0.14, 'text': 'Display response', 'shape': 'rect'},
}

# Add shapes for nodes
for node_id, node in nodes.items():
    if node['shape'] == 'rect':
        fig.add_shape(type="rect",
            x0=node['x']-0.08, y0=node['y']-0.04,
            x1=node['x']+0.08, y1=node['y']+0.04,
            line=dict(color="#21808d", width=2),
            fillcolor="#e8f4f5")
    elif node['shape'] == 'oval':
        fig.add_shape(type="circle",
            x0=node['x']-0.08, y0=node['y']-0.04,
            x1=node['x']+0.08, y1=node['y']+0.04,
            line=dict(color="#21808d", width=2),
            fillcolor="#e8f4f5")
    elif node['shape'] == 'diamond':
        # Create diamond using path
        path = f"M {node['x']},{node['y']+0.05} L {node['x']+0.09},{node['y']} L {node['x']},{node['y']-0.05} L {node['x']-0.09},{node['y']} Z"
        fig.add_shape(type="path",
            path=path,
            line=dict(color="#21808d", width=2),
            fillcolor="#e8f4f5")

# Add text annotations for nodes
for node_id, node in nodes.items():
    fig.add_annotation(
        x=node['x'], y=node['y'],
        text=node['text'],
        showarrow=False,
        font=dict(size=11, color="#13343b"),
        xanchor='center',
        yanchor='middle'
    )

# Add arrows/connections
arrows = [
    {'from': 'start', 'to': 'welcome'},
    {'from': 'welcome', 'to': 'loop'},
    {'from': 'loop', 'to': 'input'},
    {'from': 'input', 'to': 'exit_check'},
]

for arrow in arrows:
    from_node = nodes[arrow['from']]
    to_node = nodes[arrow['to']]
    fig.add_annotation(
        x=to_node['x'], y=to_node['y']+0.04,
        ax=from_node['x'], ay=from_node['y']-0.04,
        xref='x', yref='y',
        axref='x', ayref='y',
        showarrow=True,
        arrowhead=2,
        arrowsize=1,
        arrowwidth=2,
        arrowcolor="#333333"
    )

# Add Yes arrow from exit_check to goodbye
fig.add_annotation(
    x=nodes['goodbye']['x']-0.08, y=nodes['goodbye']['y'],
    ax=nodes['exit_check']['x']+0.06, ay=nodes['exit_check']['y']-0.03,
    xref='x', yref='y',
    axref='x', ayref='y',
    showarrow=True,
    arrowhead=2,
    arrowsize=1,
    arrowwidth=2,
    arrowcolor="#333333"
)
fig.add_annotation(
    x=(nodes['exit_check']['x']+nodes['goodbye']['x'])/2+0.02, 
    y=(nodes['exit_check']['y']+nodes['goodbye']['y'])/2+0.02,
    text="Yes",
    showarrow=False,
    font=dict(size=10, color="#21808d")
)

# Add arrow from goodbye to end
fig.add_annotation(
    x=nodes['end']['x'], y=nodes['end']['y']+0.04,
    ax=nodes['goodbye']['x'], ay=nodes['goodbye']['y']-0.04,
    xref='x', yref='y',
    axref='x', ayref='y',
    showarrow=True,
    arrowhead=2,
    arrowsize=1,
    arrowwidth=2,
    arrowcolor="#333333"
)

# Add No arrow from exit_check to check
fig.add_annotation(
    x=nodes['check']['x']+0.08, y=nodes['check']['y'],
    ax=nodes['exit_check']['x']-0.06, ay=nodes['exit_check']['y']-0.03,
    xref='x', yref='y',
    axref='x', ayref='y',
    showarrow=True,
    arrowhead=2,
    arrowsize=1,
    arrowwidth=2,
    arrowcolor="#333333"
)
fig.add_annotation(
    x=(nodes['exit_check']['x']+nodes['check']['x'])/2-0.02, 
    y=(nodes['exit_check']['y']+nodes['check']['y'])/2+0.02,
    text="No",
    showarrow=False,
    font=dict(size=10, color="#21808d")
)

# Add arrow from check to generate
fig.add_annotation(
    x=nodes['generate']['x'], y=nodes['generate']['y']+0.04,
    ax=nodes['check']['x'], ay=nodes['check']['y']-0.04,
    xref='x', yref='y',
    axref='x', ayref='y',
    showarrow=True,
    arrowhead=2,
    arrowsize=1,
    arrowwidth=2,
    arrowcolor="#333333"
)

# Add arrow from generate to display
fig.add_annotation(
    x=nodes['display']['x'], y=nodes['display']['y']+0.04,
    ax=nodes['generate']['x'], ay=nodes['generate']['y']-0.04,
    xref='x', yref='y',
    axref='x', ayref='y',
    showarrow=True,
    arrowhead=2,
    arrowsize=1,
    arrowwidth=2,
    arrowcolor="#333333"
)

# Add arrow from display back to loop
fig.add_annotation(
    x=nodes['loop']['x']-0.08, y=nodes['loop']['y'],
    ax=nodes['display']['x']-0.08, ay=nodes['display']['y'],
    xref='x', yref='y',
    axref='x', ayref='y',
    showarrow=True,
    arrowhead=2,
    arrowsize=1,
    arrowwidth=2,
    arrowcolor="#333333"
)

# Update layout
fig.update_layout(
    title="Rule-Based Chatbot Flow",
    xaxis=dict(visible=False, range=[0, 1]),
    yaxis=dict(visible=False, range=[0, 1.1]),
    showlegend=False,
    plot_bgcolor='#f3f3ee',
    paper_bgcolor='#f3f3ee'
)

# Save as PNG and SVG
fig.write_image('chatbot_flowchart.png')
fig.write_image('chatbot_flowchart.svg', format='svg')
#!/usr/bin/env python3
"""
Simple Rule-Based Chatbot
Author: Python Learning Example
Date: November 2025

Description:
This is a basic rule-based chatbot that uses if-elif-else statements
to respond to user inputs. The chatbot can handle greetings, questions,
and basic conversation.
"""

def chatbot():
    """
    Main chatbot function that handles user interaction through
    input/output loop and conditional statements.
    """

    print("=" * 60)
    print("Welcome to SimpleBot!")
    print("=" * 60)
    print("I'm a simple rule-based chatbot. I can chat with you!")
    print("Type 'bye', 'quit', or 'exit' to end the conversation.")
    print("-" * 60)

    # Main conversation loop - continues until user exits
    while True:
        # Get user input and convert to lowercase for easier matching
        user_input = input("\nYou: ").strip().lower()

        # Exit conditions - check if user wants to end conversation
        if user_input in ['bye', 'goodbye', 'quit', 'exit']:
            print("Bot: Goodbye! Have a great day! 👋")
            break

        # Empty input handling
        elif user_input == '':
            print("Bot: Please say something! I'm here to chat.")

        # Greetings
        elif user_input in ['hi', 'hello', 'hey', 'greetings']:
            print("Bot: Hello! How can I help you today? 😊")

        # How are you questions
        elif 'how are you' in user_input:
            print("Bot: I'm doing great! Thanks for asking. How about you?")

        # Bot identity questions
        elif 'your name' in user_input or 'who are you' in user_input:
            print("Bot: I'm SimpleBot, a rule-based chatbot created to assist you!")

        # Age questions
        elif 'how old' in user_input or 'your age' in user_input:
            print("Bot: I'm ageless! I was created recently, but age doesn't apply to bots.")

        # Help requests
        elif 'help' in user_input:
            print("Bot: I can chat with you about various topics!")
            print("     Try asking me about:")
            print("     - Greetings (hello, hi)")
            print("     - My identity (who are you, what's your name)")
            print("     - Time or weather")
            print("     - Or just chat casually!")

        # Weather questions
        elif 'weather' in user_input:
            print("Bot: I don't have access to real-time weather data,")
            print("     but I hope it's nice wherever you are! ☀️")

        # Time questions
        elif 'time' in user_input:
            import datetime
            current_time = datetime.datetime.now().strftime("%H:%M:%S")
            print(f"Bot: The current time is {current_time}. ⏰")

        # Thank you responses
        elif 'thank' in user_input:
            print("Bot: You're welcome! Happy to help! 😊")

        # Jokes
        elif 'joke' in user_input:
            print("Bot: Why do programmers prefer dark mode?")
            print("     Because light attracts bugs! 🐛😄")

        # Capabilities questions
        elif 'what can you do' in user_input or 'your capabilities' in user_input:
            print("Bot: I can:")
            print("     1. Answer basic questions")
            print("     2. Have simple conversations")
            print("     3. Tell you the time")
            print("     4. Tell jokes")
            print("     5. Provide information about myself")

        # Default response for unrecognized input
        else:
            print("Bot: I'm not sure I understand that.")
            print("     Could you rephrase or type 'help' for options?")


# Main execution
if __name__ == "__main__":
    chatbot()
    #!/usr/bin/env python3
"""
Advanced Rule-Based Chatbot with Multiple Features
Author: Python Learning Example
Date: November 2025

Description:
An enhanced rule-based chatbot with conversation history tracking,
randomized responses, and multiple conversation domains.
"""

import random
import datetime


class AdvancedChatbot:
    """
    Advanced chatbot class with conversation history and
    multiple response options.
    """

    def __init__(self, bot_name="AdvancedBot"):
        """Initialize the chatbot with name and conversation history."""
        self.bot_name = bot_name
        self.conversation_history = []
        self.user_name = None

        # Response dictionaries for varied responses
        self.greetings = [
            "Hello! How can I assist you today?",
            "Hi there! What can I do for you?",
            "Hey! Great to see you!",
            "Greetings! How may I help you?"
        ]

        self.goodbyes = [
            "Goodbye! Take care!",
            "See you later! Have a great day!",
            "Bye! Come back anytime!",
            "Farewell! It was nice chatting with you!"
        ]

        self.thanks_responses = [
            "You're welcome! Happy to help!",
            "No problem at all!",
            "Glad I could assist you!",
            "Anytime! That's what I'm here for!"
        ]

        # Domain-specific knowledge
        self.programming_topics = {
            'python': "Python is a versatile programming language known for its simplicity and readability!",
            'javascript': "JavaScript powers the web! It's essential for frontend development.",
            'java': "Java is a robust, object-oriented language used in enterprise applications.",
            'c++': "C++ is powerful for system programming and game development!",
            'sql': "SQL is the standard language for database management and queries."
        }

        self.jokes = [
            ("Why do programmers prefer dark mode?", "Because light attracts bugs! 🐛"),
            ("Why was the JavaScript developer sad?", "Because he didn't Node how to Express himself! 😄"),
            ("What's a programmer's favorite hangout place?", "The Foo Bar! 🍺"),
            ("Why do Python programmers wear glasses?", "Because they can't C! 👓"),
            ("How many programmers does it take to change a light bulb?", "None. It's a hardware problem! 💡")
        ]

    def add_to_history(self, user_input, bot_response):
        """Store conversation in history."""
        timestamp = datetime.datetime.now().strftime("%H:%M:%S")
        self.conversation_history.append({
            'time': timestamp,
            'user': user_input,
            'bot': bot_response
        })

    def show_history(self):
        """Display conversation history."""
        if not self.conversation_history:
            return "No conversation history yet!"

        history_text = "\n📜 Conversation History:\n" + "=" * 50
        for entry in self.conversation_history[-5:]:  # Show last 5 exchanges
            history_text += f"\n[{entry['time']}]"
            history_text += f"\n  You: {entry['user']}"
            history_text += f"\n  Bot: {entry['bot']}"
        return history_text

    def get_response(self, user_input):
        """
        Generate appropriate response based on user input
        using if-elif-else conditional logic.
        """

        # Convert to lowercase for easier matching
        user_input_lower = user_input.strip().lower()
        response = ""

        # Exit conditions
        if user_input_lower in ['bye', 'goodbye', 'quit', 'exit', 'see you']:
            response = random.choice(self.goodbyes)
            if self.user_name:
                response = f"{response} {self.user_name}! 👋"

        # Empty input
        elif user_input_lower == '':
            response = "Please say something! I'm listening. 👂"

        # Name introduction
        elif 'my name is' in user_input_lower:
            # Extract name after "my name is"
            name_parts = user_input_lower.split('my name is')
            if len(name_parts) > 1:
                self.user_name = name_parts[1].strip().title()
                response = f"Nice to meet you, {self.user_name}! 😊"

        # Greetings
        elif user_input_lower in ['hi', 'hello', 'hey', 'greetings', 'howdy']:
            response = random.choice(self.greetings)
            if self.user_name:
                response = response.replace('!', f', {self.user_name}!')

        # How are you
        elif 'how are you' in user_input_lower:
            response = "I'm functioning perfectly! Thanks for asking. How about you?"

        # Bot identity
        elif 'your name' in user_input_lower or 'who are you' in user_input_lower:
            response = f"I'm {self.bot_name}, your friendly rule-based chatbot assistant!"

        # Help command
        elif user_input_lower == 'help':
            response = """🆘 Available Commands:

1. Greetings: Say 'hello', 'hi', 'hey'
2. Identity: Ask 'what is your name' or 'who are you'
3. Time: Ask 'what time is it'
4. Date: Ask 'what's the date'
5. Math: Ask 'calculate [expression]' (e.g., 'calculate 5 + 3')
6. Programming: Ask about python, java, javascript, c++, sql
7. Jokes: Type 'joke' or 'tell me a joke'
8. History: Type 'history' to see conversation history
9. Exit: Type 'bye', 'quit', or 'exit' to end chat
"""

        # Time query
        elif 'time' in user_input_lower and 'what' in user_input_lower:
            current_time = datetime.datetime.now().strftime("%I:%M %p")
            response = f"The current time is {current_time}. ⏰"

        # Date query
        elif 'date' in user_input_lower and 'what' in user_input_lower:
            current_date = datetime.datetime.now().strftime("%B %d, %Y")
            response = f"Today's date is {current_date}. 📅"

        # Day of week
        elif 'day' in user_input_lower and 'what' in user_input_lower:
            day = datetime.datetime.now().strftime("%A")
            response = f"Today is {day}!"

        # Math calculations
        elif 'calculate' in user_input_lower or 'solve' in user_input_lower:
            try:
                # Extract expression after 'calculate' or 'solve'
                expression = user_input_lower.split('calculate')[-1].split('solve')[-1].strip()
                # Safely evaluate mathematical expression
                result = eval(expression, {"__builtins__": {}}, {})
                response = f"The answer is: {result} 🧮"
            except:
                response = "I couldn't calculate that. Please use format: 'calculate 5 + 3'"

        # Programming language queries
        elif any(lang in user_input_lower for lang in self.programming_topics.keys()):
            for lang, info in self.programming_topics.items():
                if lang in user_input_lower:
                    response = info
                    break

        # Jokes
        elif 'joke' in user_input_lower:
            joke_setup, joke_punchline = random.choice(self.jokes)
            response = f"{joke_setup}\n     {joke_punchline}"

        # Conversation history
        elif 'history' in user_input_lower:
            response = self.show_history()

        # Thank you
        elif 'thank' in user_input_lower:
            response = random.choice(self.thanks_responses)

        # Capabilities
        elif 'what can you do' in user_input_lower or 'capabilities' in user_input_lower:
            response = """I can do many things! 🤖

✅ Answer questions about programming languages
✅ Perform basic calculations
✅ Tell you the time and date
✅ Tell jokes to brighten your day
✅ Keep track of our conversation history
✅ Have casual conversations

Type 'help' for detailed commands!"""

        # Weather (limitation acknowledgment)
        elif 'weather' in user_input_lower:
            response = "I don't have access to real-time weather data, but I hope it's pleasant! ⛅"

        # Age question
        elif 'how old' in user_input_lower or 'age' in user_input_lower:
            response = "I'm timeless! Created in 2025, but age is just a number for bots. 🤖"

        # Compliments
        elif any(word in user_input_lower for word in ['good', 'great', 'awesome', 'excellent']):
            response = "Thank you! I appreciate your kind words! 😊"

        # Default fallback
        else:
            response = """I'm not sure I understand that. 🤔

Try asking me about:
- Programming languages (Python, Java, JavaScript, etc.)
- Time or date
- Calculations (e.g., 'calculate 10 * 5')
- Or type 'help' for all available commands!"""

        # Add to conversation history
        self.add_to_history(user_input, response)

        return response

    def run(self):
        """Main chatbot loop."""
        print("=" * 70)
        print(f"    Welcome to {self.bot_name}!")
        print("=" * 70)
        print("I'm an advanced rule-based chatbot with multiple capabilities!")
        print("Type 'help' to see what I can do, or 'bye' to exit.")
        print("-" * 70)

        while True:
            try:
                user_input = input("\nYou: ").strip()

                if not user_
  input:
                    continue

                response = self.get_response(user_input)
                print(f"Bot: {response}")

                # Check if user wants to exit
                if user_input.lower() in ['bye', 'goodbye', 'quit', 'exit']:
                    break

            except KeyboardInterrupt:
                print("\n\nBot: Interrupted! Goodbye! 👋")
                break
            except Exception as e:
                print(f"Bot: Oops! An error occurred: {e}")


# Main execution
if __name__ == "__main__":
    bot = AdvancedChatbot("SmartBot")
    bot.run()
    
