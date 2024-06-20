# ik-demo


# requirements.txt
```text
openai
python-dotenv
streamlit
```
# create project folder
```bash
mkdir ik-demo
cd ik-demo
```

# python virtual environment

```bash
python3 -m venv ik-demo
```

# activate python virtual environment
```bash
source bin/activate
```


# sample questions

```python
assignments = [
    "FizzBuzz",
    "Reverse a string",
    "Calculate factorial of a number",
    "Check if a string is a palindrome",
    "Find the largest element in an array",
    "Sort an array of integers",
    "Implement a stack using a list",
    "Implement a queue using two stacks",
    "Binary search on a sorted array",
    "Count the number of vowels in a string",
    "Find the Fibonacci sequence up to N",
    "Check if a number is prime",
    "Convert decimal to binary",
    "Implement bubble sort algorithm",
    "Implement selection sort algorithm",
    "Implement insertion sort algorithm"
]
```

# streamlit app.py
```python
import streamlit as st
from openai import OpenAI
from dotenv import load_dotenv
import time
import base64
from io import BytesIO
import os
from dotenv import load_dotenv
from google.cloud import storage
from google.cloud import bigquery

# Load environment variables from .env file
load_dotenv()

# Access the API key using the variable name defined in the .env file
key = os.getenv("OPENAI_API_KEY")

# Create OpenAI Client

client = OpenAI(api_key=key)

# Paste Streamlit code here
import streamlit as st

# List of programming assignments
assignments = [
    "FizzBuzz",
    "Reverse a string",
    "Calculate factorial of a number",
    "Check if a string is a palindrome",
    "Find the largest element in an array",
    "Sort an array of integers",
    "Implement a stack using a list",
    "Implement a queue using two stacks",
    "Binary search on a sorted array",
    "Count the number of vowels in a string",
    "Find the Fibonacci sequence up to N",
    "Check if a number is prime",
    "Convert decimal to binary",
    "Implement bubble sort algorithm",
    "Implement selection sort algorithm",
    "Implement insertion sort algorithm"
]
st.image('logo.png')
st.subheader("Select a CS topic")
# Create a dropdown in Streamlit
selected_assignment = st.selectbox("Select an assignment", assignments)

# Display the selected assignment
st.write("You selected:", selected_assignment)

# st.header("OpenAI Embeddings")
# response = client.embeddings.create(
#     input=selected_assignment,
#     model="text-embedding-3-small"
# )

# st.write(response.data[0].embedding)

prompt = f"Give a simple explanation and solution narrative for the following {selected_assignment}"

st.subheader("Prompt")
st.write(f"Give a simple explanation and solution narrative for the following {selected_assignment}")


response = client.chat.completions.create(
model="gpt-4o",
messages=[
    {
    "role": "user",
    "content": [
        {"type": "text", "text": prompt},
        # {
        # "type": "image_url",
        # "image_url": {
        #     "url": public_url,
        # },
        # },
    ],
    }
],
# max_tokens=300,
)

st.markdown(response.choices[0].message.content.strip()) 

prompt2 = f"Give a simple explanation and solution narrative for the following {selected_assignment}"

narration = client.chat.completions.create(

model="gpt-4o",
messages=[
    {
    "role": "user",
    "content": [
        {"type": "text", "text": prompt2},
        # {
        # "type": "image_url",
        # "image_url": {
        #     "url": public_url,
        # },
        # },
    ],
    }
],
# max_tokens=300,
)
st.subheader("Listen to summary...take a moment to generate")
response = client.audio.speech.create(
model="tts-1",
voice="alloy",
input=str(narration.choices[0].message.content.strip()),
)

response.stream_to_file("output.mp3")

st.audio("output.mp3", format="audio/mpeg", loop=False)


```

# Run Streamlit
```bash
streamlit run app.py
```
