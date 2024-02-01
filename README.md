## LokaTechAssessment

This code is designed for leveraging language models and embeddings to perform question-answering on a given set of documents. The following steps outline the functionality and usage of the code:

### Requirements
Python
Required Python packages are listed in the code comments. You can install them using a package manager like pip.
### Setup
Import necessary modules and libraries.
Set the environment variable HUGGING_FACE_HUB_API_KEY with the API key for accessing the Hugging Face API.
Define the path to the directory containing documents (sagemaker_doc_path).
Loading Documents
Load documents from the specified directory using DirectoryLoader and TextLoader.
Text Processing
Use RecursiveCharacterTextSplitter to split the documents into smaller chunks, facilitating efficient processing.
Embeddings and Vector Database
Initialize embeddings using Hugging Face models (HuggingFaceEmbeddings).
Create a vector database (Chroma) from the document chunks, and optionally save it to disk.
Language Model
Create a pre-trained language model (HuggingFaceHub) for text generation and question-answering.
Retrieval Chain
Set up a retrieval chain (RetrievalQA) with the language model and the vector database as retriever.
Processing Responses
Define functions for processing and printing the question, answer, and sources.
Usage Example
python
Copy code
# Example usage of the retrieval chain and response processing
response = retrieval_chain.process_query("Your question goes here?")
process_llm_response(response)
Note
The code utilizes Hugging Face models and their hub for language model retrieval.
The retrieval chain is set up for a specific chain type ('stuff') with configurable parameters.
Sources are extracted and printed for transparency.
Important
Ensure that the Hugging Face API key is kept secure and not shared publicly.
Some parts of the code are commented out for optional features (e.g., loading vector database from disk).
