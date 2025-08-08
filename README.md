<xaiArtifact artifact_id="0be5f3f4-2580-4eab-a024-cae256529394" artifact_version_id="033f35c7-19bd-40cf-9a0d-646e432a7911" title="README.md" contentType="text/markdown">

# Exploring the Awesome ChatGPT Prompts Dataset 🤖📚

This README provides a comprehensive guide to loading and exploring the `awesome-chatgpt-prompts` dataset from the Hugging Face Hub using two different approaches: the **Hugging Face Datasets Library** and the **Hugging Face Hub Library**. The dataset, hosted at `fka/awesome-chatgpt-prompts`, contains creative prompts for ChatGPT, and we’ll walk through how to access and inspect it step-by-step. 🚀

---

## 📋 Table of Contents
1. [Overview](#overview-)
2. [Prerequisites](#prerequisites-)
3. [Method 1: Using the Datasets Library](#method-1-using-the-datasets-library-)
   - [Step-by-Step Instructions](#step-by-step-instructions-for-method-1)
   - [Code Snippet](#code-snippet-for-method-1)
4. [Method 2: Using the Hugging Face Hub Library](#method-2-using-the-hugging-face-hub-library-)
   - [Step-by-Step Instructions](#step-by-step-instructions-for-method-2)
   - [Code Snippet](#code-snippet-for-method-2)
5. [Expected Output](#expected-output-)
6. [Notes and Tips](#notes-and-tips-)
7. [References](#references-)

---

## Overview 🌟
The `awesome-chatgpt-prompts` dataset, available on the Hugging Face Hub, is a collection of creative and useful prompts designed for ChatGPT. This dataset is ideal for researchers, developers, and enthusiasts looking to experiment with prompt engineering or fine-tune language models. The dataset is structured as a Hugging Face Dataset, making it easy to load and explore programmatically.

We’ll demonstrate two methods to load this dataset:
- **Method 1**: Using the `datasets` library, which is the preferred approach for datasets formatted as Hugging Face Dataset repositories.
- **Method 2**: Using the `huggingface_hub` library, which provides an alternative way to authenticate and load datasets.

Both methods will allow you to load the dataset and inspect its contents using pandas for a tabular view of the data.

---

## Prerequisites 🛠️
Before you begin, ensure you have the following:
- **Python 3.7+** installed.
- A working installation of `pip` for installing Python packages.
- An active Hugging Face account (for Method 2, to authenticate with the Hub).
- Basic familiarity with Python and Jupyter notebooks or a Python IDE.

Install the required libraries:
```bash
pip install datasets huggingface_hub pandas
```

---

## Method 1: Using the Datasets Library 📊

The `datasets` library from Hugging Face is the preferred method for loading datasets that are formatted and published as Dataset repositories on the Hugging Face Hub. This method is straightforward and doesn’t require explicit authentication for public datasets like `fka/awesome-chatgpt-prompts`.

### Step-by-Step Instructions for Method 1
1. **Install the Datasets Library**:
   - Run the following command to install the `datasets` library if not already installed:
     ```bash
     pip install datasets
     ```
2. **Import the Library**:
   - Import the `load_dataset` function from the `datasets` library.
3. **Load the Dataset**:
   - Use the `load_dataset` function to fetch the `fka/awesome-chatgpt-prompts` dataset.
4. **Explore the Dataset**:
   - Convert the dataset’s `train` split to a pandas DataFrame and display the first and last five rows using `.head()` and `.tail()`.
   - Access individual examples using indexing.

### Code Snippet for Method 1
```python
# Install the datasets library (run in terminal or notebook cell)
!pip install datasets

# Import the necessary library
from datasets import load_dataset

# Load the dataset
ds = load_dataset("fka/awesome-chatgpt-prompts")

# Display the first 5 rows
print("----- HEAD (First 5 rows) -----")
print(ds['train'].to_pandas().head())

# Display the last 5 rows
print("\n----- TAIL (Last 5 rows) -----")
print(ds['train'].to_pandas().tail())

# Print the first example
print("\n----- First Example -----")
print(ds['train'][0])
```

---

## Method 2: Using the Hugging Face Hub Library 🔐

The `huggingface_hub` library allows you to authenticate with the Hugging Face Hub and load datasets. This method is useful when you need to access private datasets or prefer explicit authentication.

### Step-by-Step Instructions for Method 2
1. **Install the Hugging Face Hub Library**:
   - Install the `huggingface_hub` library and ensure it’s up-to-date:
     ```bash
     pip install huggingface_hub
     pip install --upgrade huggingface_hub
     ```
2. **Authenticate with Hugging Face**:
   - Log in to the Hugging Face Hub using your API token. You can obtain your token from your Hugging Face account settings.
   - Use the `huggingface_hub` login function or the CLI command `huggingface-cli login`.
3. **Load the Dataset**:
   - Use the `datasets` library’s `load_dataset` function (same as Method 1) after authentication.
4. **Explore the Dataset**:
   - Convert the dataset to a pandas DataFrame and display the first and last five rows.

### Code Snippet for Method 2
```python
# Install the required libraries (run in terminal or notebook cell)
!pip install huggingface_hub
!pip install --upgrade huggingface_hub

# Authenticate with Hugging Face Hub
from huggingface_hub import login
login()  # You will be prompted to enter your Hugging Face API token

# Import the necessary library
from datasets import load_dataset

# Load the dataset
dataset = load_dataset("fka/awesome-chatgpt-prompts")

# Display the first 5 rows
print("----- HEAD (First 5 rows) -----")
print(dataset["train"].to_pandas().head())

# Display the last 5 rows
print("\n----- TAIL (Last 5 rows) -----")
print(dataset["train"].to_pandas().tail())
```

**Note**: For public datasets like `fka/awesome-chatgpt-prompts`, authentication is optional. However, running `login()` ensures compatibility with private datasets or restricted access scenarios.

---

## Expected Output 📈

Running either method will produce output similar to the following (actual content may vary slightly based on dataset updates):

### HEAD (First 5 rows)
```
   act                                      prompt
0  Linux Terminal  I want you to act as a Linux Terminal. I will type commands and you will reply with what the terminal should show. ...
1  English Translator  I want you to act as an English translator, spelling corrector, and improver. I will provide text in any language, and you will translate it into English. ...
2  Interviewer  I want you to act as an interviewer. I will be the candidate, and you will ask me questions for the position of [insert position]. ...
3  JavaScript Console  I want you to act as a JavaScript console. I will provide JavaScript code, and you will show the output as a console would. ...
4  Excel Sheet  I want you to act as an Excel sheet. I will provide formulas or data, and you will calculate or display the results as Excel would. ...
```

### TAIL (Last 5 rows)
```
     act                                      prompt
148  Motivational Coach  I want you to act as a motivational coach. Provide me with encouragement and actionable advice to achieve my goals. ...
149  Travel Guide  I want you to act as a travel guide. I will provide my destination, and you will suggest an itinerary and tips. ...
150  Storyteller  I want you to act as a storyteller. Create a short story based on the genre and characters I provide. ...
151  Debate Coach  I want you to act as a debate coach. Help me prepare arguments for a given topic and suggest counterarguments. ...
152  Creative Writer  I want you to act as a creative writer. Write a poem, story, or script based on the theme I provide. ...
```

### First Example
```python
{'act': 'Linux Terminal', 'prompt': 'I want you to act as a Linux Terminal. I will type commands and you will reply with what the terminal should show. ...'}
```

---

## Notes and Tips 📝
- **Dataset Structure**: The `awesome-chatgpt-prompts` dataset typically has a `train` split with columns like `act` (the role or persona) and `prompt` (the instruction for ChatGPT).
- **Authentication**: For Method 2, ensure you have a valid Hugging Face API token. You can generate one from your Hugging Face account settings.
- **Performance**: The `datasets` library is optimized for large datasets and provides efficient data loading and processing compared to raw file downloads.
- **Environment**: Run the code in a Jupyter notebook or a Python script. Ensure `pandas` is installed for DataFrame conversions (`pip install pandas`).
- **Public Dataset**: Since `fka/awesome-chatgpt-prompts` is public, Method 1 is simpler as it skips authentication.

---

## References 🔗
- [Hugging Face Datasets Documentation](https://huggingface.co/docs/datasets/)
- [Hugging Face Hub Documentation](https://huggingface.co/docs/huggingface_hub/)
- [Awesome ChatGPT Prompts Dataset](https://huggingface.co/datasets/fka/awesome-chatgpt-prompts)

Happy exploring! 🎉

</xaiArtifact>
