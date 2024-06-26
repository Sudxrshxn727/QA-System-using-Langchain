# Codebasics QA System

This project is a Question-Answer (QA) system for customer query and issue searching on the Codebasics edtech platform. The system is built using Langchain, Streamlit, and Google Palm LLM to provide automated responses to customer queries based on a preloaded dataset of questions and answers.

## Features

- **Automated Query Response**: Provides automated responses to customer queries using an LLM.
- **Knowledge Base Generation**: Generates a vector database of customer queries and answers for efficient retrieval.
- **Streamlit Interface**: User-friendly interface for interacting with the QA system.

## Project Structure

The project consists of three main files:

1. **main.py**: Contains the Streamlit code for the user interface.
2. **lang.py**: Handles data connection, vector database creation, LLM model integration, and prompt template definition.
3. **.env**: Stores the API key for Google Palm.

## Installation

### Prerequisites

- Python 3.8 or higher
- Streamlit
- Langchain
- Google Palm API key

### Steps

1. **Clone the repository**:
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```

2. **Install the required libraries**:
    ```bash
    pip install streamlit langchain python-dotenv
    ```

3. **Setup the .env file**:
    - Create a `.env` file in the project directory.
    - Add your Google Palm API key to the `.env` file:
      ```
      GOOGLE_PALM_API_KEY=your_api_key_here
      ```

4. **Prepare the CSV file**:
    - Ensure you have a CSV file containing customer queries and answers stored in the project directory.

5. **Run the Streamlit app**:
    ```bash
    streamlit run main.py
    ```

## Usage

### Generating the Knowledge Base

1. Open the Streamlit app in your browser.
2. Click the "Generate Knowledge Base" button to create the vector database from the CSV file containing customer queries and answers.

### Querying the QA System

1. Enter your query in the text input field.
2. The system uses the vector database to find the most relevant answer based on the provided query and displays the response.

## Code Overview

### Imports

```python
from dotenv import load_dotenv
from langchain.chains import RetrievalQA
from langchain.document_loaders.csv_loader import CSVLoader
from langchain.llms import GooglePalm
from langchain.prompts import PromptTemplate
from langchain.vectorstores import FAISS
import streamlit as st
```

### lang.py

- **API Connection**: Connects to the Google Palm API using the key from the `.env` file.
- **Data Source**: Loads customer queries and answers from a CSV file.
- **Vector Database**: Uses FAISS to create a vector database of the questions and answers.
- **Embeddings**: Utilizes Google Palm embeddings for creating vector representations of the text.
- **Functions**:
  - `create_vector_db`: Generates the vector database.
  - `get_qa_chain`: Retrieves answers to queries using the vector database and prompt template.

### main.py

- **Streamlit UI**:
  - **Generate Knowledge Base Button**: Linked to `create_vector_db` function.
  - **Query Input Field**: Connected to the `get_qa_chain` function to provide automated responses based on the vector database.

## Conclusion

The Codebasics QA System provides an efficient way to automate the response process for customer queries using advanced language models and vector databases. This reduces the manual effort required to answer repetitive queries and provides quick, accurate responses.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

## Acknowledgements

- [Langchain](https://langchain.com/)
- [Streamlit](https://streamlit.io/)
- [Google Palm](https://cloud.google.com/palm)

Feel free to contribute to this project by opening issues or submitting pull requests.
