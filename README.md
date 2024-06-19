# ik-demo


# requirements.txt
```text
openai
python-dotenv
streamlit
```
# python virtual environment

```bash
python3 -m venv ik-demo
```

# activate python virtual environment
```bash
source bin/activate
```

# app.py
```python

from openai import OpenAI
import streamlit as st
import python-dotenv
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

# streamlit dropdown
```python
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

# Create a dropdown in Streamlit
selected_assignment = st.selectbox("Select an assignment", assignments)

# Display the selected assignment
st.write("You selected:", selected_assignment)

```

# Run Streamlit
```bash
streamlit run app.py
```
