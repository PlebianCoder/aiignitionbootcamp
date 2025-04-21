# Prompt Engineering Whitepaper

## Introduction

Prompt engineering is the art and science of crafting effective prompts to guide Large Language Models (LLMs) like Gemini, GPT, Claude, and others. This whitepaper provides a comprehensive overview of prompt engineering techniques, LLM output configuration, best practices, and practical examples for software engineers and AI practitioners.

---

## Table of Contents

1. [Introduction](#introduction)
2. [LLM Output Configuration](#llm-output-configuration)
3. [Prompting Techniques](#prompting-techniques)
    - Zero-shot, One-shot, Few-shot
    - System, Contextual, and Role Prompting
    - Step-back Prompting
    - Chain of Thought (CoT)
    - Self-consistency
    - Tree of Thoughts (ToT)
    - ReAct (Reason & Act)
    - Automatic Prompt Engineering (APE)
4. [Code Prompting](#code-prompting)
    - Writing Code
    - Explaining Code
    - Translating Code
    - Debugging and Reviewing Code
5. [Best Practices](#best-practices)
6. [Summary](#summary)
7. [Endnotes](#endnotes)

---

## LLM Output Configuration

LLMs offer several configuration options that control their output:

- **Output Length:** Number of tokens to generate. More tokens = more computation, higher cost.
- **Temperature:** Controls randomness. Lower = more deterministic, higher = more creative.
- **Top-K:** Restricts output to the top K most likely tokens.
- **Top-P (Nucleus Sampling):** Restricts output to the smallest set of tokens whose cumulative probability exceeds P.

**Example Settings:**

| Setting      | Typical Value | Effect                        |
|-------------|--------------|-------------------------------|
| Temperature | 0.1 - 0.9    | Lower = deterministic, higher = creative |
| Top-K       | 20 - 40      | Higher = more creative        |
| Top-P       | 0.9 - 0.99   | Higher = more creative        |

---

## Prompting Techniques

### Zero-shot Prompting

A simple prompt with no examples. Useful for straightforward tasks.

**Example:**
```
Classify movie reviews as POSITIVE, NEUTRAL or NEGATIVE.
Review: "Her" is a disturbing study revealing the direction humanity is headed if AI is allowed to keep evolving, unchecked. I wish there were more movies like this masterpiece.
Sentiment:
```
**Output:**
```
POSITIVE
```

### One-shot & Few-shot Prompting

Provide one or more examples to guide the model.

**Few-shot Example:**
| Goal | Parse pizza orders to JSON |
|------|---------------------------|
| Prompt | Parse a customer's pizza order into valid JSON:
EXAMPLE:
"I want a small pizza with cheese, tomato sauce, and pepperoni."
JSON Response:
{
  "size": "small",
  "type": "normal",
  "ingredients": [["cheese", "tomato sauce", "peperoni"]]
}
EXAMPLE:
"Can I get a large pizza with tomato sauce, basil and mozzarella"
JSON Response:
{
  "size": "large",
  "type": "normal",
  "ingredients": [["tomato sauce", "bazel", "mozzarella"]]
}
Now, I would like a large pizza, with the first half cheese and mozzarella. And the other tomato sauce, ham and pineapple.
JSON Response:
|
| Output | {
  "size": "large",
  "type": "half-half",
  "ingredients": [["cheese", "mozzarella"], ["tomato sauce", "ham", "pineapple"]]
}
|

### System, Contextual, and Role Prompting

- **System Prompting:** Sets the overall context and purpose.
- **Contextual Prompting:** Provides specific details or background.
- **Role Prompting:** Assigns a persona or style to the model.

**System Example:**
```
Classify movie reviews as positive, neutral or negative. Only return the label in uppercase.
Review: "Her" is a disturbing study revealing the direction humanity is headed if AI is allowed to keep evolving, unchecked. It's so disturbing I couldn't watch it.
Sentiment:
```
**Output:**
```
NEGATIVE
```

**Role Example:**
```
I want you to act as a travel guide. I will write to you about my location and you will suggest 3 places to visit near me in a humorous style.
My suggestion: "I am in Manhattan."
Travel Suggestions:
```
**Output:**
1. Behold the Empire State of Mind: ...
2. Get Artsy-Fartsy at MoMA: ...
3. Shop 'Til You Drop on Fifth Avenue: ...

### Step-back Prompting

Encourages the model to consider a general question before a specific one.

**Example:**
1. Ask: "What are 5 key settings for a first-person shooter video game?"
2. Use the answer as context for: "Write a one paragraph storyline for a new level set in an underwater research facility."

### Chain of Thought (CoT)

Instructs the model to reason step by step.

**Example:**
```
When I was 3 years old, my partner was 3 times my age. Now, I am 20 years old. How old is my partner? Let's think step by step.
```
**Output:**
1. When I was 3, my partner was 9.
2. Now I am 20, so 17 years have passed.
3. My partner is now 9 + 17 = 26 years old.

### Self-consistency

Run the same prompt multiple times with high temperature, then select the most common answer.

### Tree of Thoughts (ToT)

Allows the model to explore multiple reasoning paths simultaneously, not just a single chain.

### ReAct (Reason & Act)

Combines reasoning with actions, such as using external tools or APIs.

**Example:**
- The model reasons about a problem, performs a search, updates its reasoning, and repeats until a solution is found.

### Automatic Prompt Engineering (APE)

Automates the creation and evaluation of prompts by having the model generate and score prompt variants.

---

## Code Prompting

### Writing Code

**Prompt:**
```
Write a code snippet in Bash, which asks for a folder name. Then it takes the contents of the folder and renames all the files inside by prepending the name draft to the file name.
```
**Output:**
```bash
#!/bin/bash
echo "Enter the folder name:"
read folder_name
if [ ! -d "$folder_name" ]; then
  echo "Folder does not exist."
  exit 1
fi
files=("$folder_name"/*)
for file in "${files[@]}"; do
  new_file_name="draft_$(basename "$file")"
  mv "$file" "$new_file_name"
done
echo "Files renamed successfully."
```

### Explaining Code

**Prompt:**
```
Explain to me the below Bash code:
#!/bin/bash
echo "Enter the folder name:"
read folder_name
...
```
**Output:**
1. Prompts the user for a folder name.
2. Checks if the folder exists.
3. Lists files and renames them with a prefix.
4. Prints a success message.

### Translating Code

**Prompt:**
```
Translate the below Bash code to a Python snippet.
...
```
**Output:**
```python
import os
import shutil
folder_name = input("Enter the folder name: ")
if not os.path.isdir(folder_name):
    print("Folder does not exist.")
    exit(1)
files = os.listdir(folder_name)
for file in files:
    new_file_name = f"draft_{file}"
    shutil.move(os.path.join(folder_name, file), os.path.join(folder_name, new_file_name))
print("Files renamed successfully.")
```

### Debugging and Reviewing Code

**Prompt:**
```
The below Python code gives an error:
...
Debug what's wrong and explain how I can improve the code.
```
**Output:**
- Identifies undefined functions or errors.
- Suggests corrections and improvements.
- Provides improved code with error handling.

---

## Best Practices

- **Provide Examples:** Use one-shot or few-shot examples to teach the model.
- **Design with Simplicity:** Keep prompts concise and clear.
- **Be Specific About Output:** Clearly state the desired format and content.
- **Use Instructions Over Constraints:** Prefer positive instructions to lists of what not to do.
- **Control Max Token Length:** Set limits in configuration or prompt.
- **Use Variables in Prompts:** Make prompts reusable and dynamic.
- **Experiment with Input/Output Formats:** Try different styles and formats.
- **Mix Up Classes in Few-shot Prompts:** Avoid overfitting to example order.
- **Adapt to Model Updates:** Adjust prompts for new model versions.
- **Document Prompt Attempts:** Track prompt versions, results, and feedback.

---

## Summary

This whitepaper covers:
- Prompt engineering fundamentals
- LLM output configuration
- Prompting techniques (zero-shot, few-shot, system, role, CoT, ToT, ReAct, APE)
- Code prompting and debugging
- Best practices for effective prompting

Prompt engineering is an iterative process. Craft, test, analyze, and refine prompts to achieve the best results. Document your work and stay updated with new models and techniques.

---

## Endnotes

1. Google, 2023, Gemini by Google. [https://gemini.google.com](https://gemini.google.com)
2. Google, 2024, Gemini for Google Workspace Prompt Guide. [link](https://inthecloud.withgoogle.com/gemini-for-google-workspace-prompt-guide/dl-cd.html)
3. Google Cloud, 2023, Introduction to Prompting. [link](https://cloud.google.com/vertex-ai/generative-ai/docs/learn/prompts/introduction-prompt-design)
4. Google Cloud, 2023, Text Model Request Body: Top-P & top-K sampling methods. [link](https://cloud.google.com/vertex-ai/docs/generative-ai/model-reference/text#request_body)
5. Wei, J., et al., 2023, Zero Shot - Fine Tuned language models are zero shot learners. [arxiv](https://arxiv.org/pdf/2109.01652.pdf)
6. Google Cloud, 2023, Google Cloud Model Garden. [link](https://cloud.google.com/model-garden)
7. Brown, T., et al., 2023, Few Shot - Language Models are Few Shot learners. [arxiv](https://arxiv.org/pdf/2005.14165.pdf)
8. Zheng, L., et al., 2023, Take a Step Back: Evoking Reasoning via Abstraction in Large Language Models. [openreview](https://openreview.net/pdf?id=3bq3jsvcQ1)
9. Wei, J., et al., 2023, Chain of Thought Prompting. [arxiv](https://arxiv.org/pdf/2201.11903.pdf)
10. Google Cloud Platform, 2023, Chain of Thought and React. [github](https://github.com/GoogleCloudPlatform/generative-ai/blob/main/language/prompts/examples/chain_of_thought_react.ipynb)
11. Wang, X., et al., 2023, Self Consistency Improves Chain of Thought reasoning in language models. [arxiv](https://arxiv.org/pdf/2203.11171.pdf)
12. Yao, S., et al., 2023, Tree of Thoughts: Deliberate Problem Solving with Large Language Models. [arxiv](https://arxiv.org/pdf/2305.10601.pdf)
13. Yao, S., et al., 2023, ReAct: Synergizing Reasoning and Acting in Language Models. [arxiv](https://arxiv.org/pdf/2210.03629.pdf)
14. Google Cloud Platform, 2023, Advance Prompting: Chain of Thought and React. [github](https://github.com/GoogleCloudPlatform/applied-ai-engineering-samples/blob/main/genai-on-vertex-ai/advanced_prompting_training/cot_react.ipynb)
15. Zhou, C., et al., 2023, Automatic Prompt Engineering - Large Language Models are Human-Level Prompt Engineers. [arxiv](https://arxiv.org/pdf/2211.01910.pdf)

Let me know if you need anything else\!