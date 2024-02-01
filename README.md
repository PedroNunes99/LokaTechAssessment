## LokaTechAssessment

This POC is designed for assisting developers in unfamiliar documentation areas, significantly reducing the time spent searching for information. It follows a question-answering approach, allowing users to pose questions to the system related to the uploaded documentation. The system responds with accurate answers in natural language, accompanied by references to the source documents that informed the response.

### Architecture of the system
The system architecture adopts a Retrieval-Augmented Generation (RAG) approach, incorporating an information retrieval component. This component utilizes user input to initially retrieve information from a new data source. Further details on the architecture's functionality are provided above. 
<img width="1569" alt="Screenshot 2024-02-01 at 11 35 07" src="https://github.com/PedroNunes99/LokaTechAssessment/assets/44478888/f2152d8b-8130-4338-bbbc-6c4c55cd66f6">

### Requirements
Python
Required Python packages are listed in the code.
### Setup
Import necessary modules and libraries.
Set the environment variable HUGGING_FACE_HUB_API_KEY with the API key for accessing the Hugging Face API.
Define the path to the directory containing documents (sagemaker_doc_path).
If using google colab, upload manually the zip file present in the repository before runnning the unzip command available in the code.
### Loading Documents
Load documents from the specified directory using DirectoryLoader and TextLoader.
### Text Processing
Use RecursiveCharacterTextSplitter to split the documents into smaller chunks, facilitating efficient processing.
### Embeddings and Vector Database
Initialize embeddings using Hugging Face models (HuggingFaceEmbeddings).
Create a vector database (Chroma) from the document chunks, and optionally save it to disk.
### Language Model
Import a pre-trained language model (from HuggingFaceHub) for text generation and question-answering.
### Retrieval Chain
Set up a retrieval chain (RetrievalQA) with the language model and the vector database as retriever.
### Processing Responses
Define functions for processing and printing the question, answer, and sources.
### Usage Example
```
query1 = "What is SageMaker?"
process_llm_response(retrieval_chain.invoke(query1))
```
Output:
```
Question:  What is SageMaker?

Answer:   SageMaker is a fully managed machine learning service that enables data scientists and developers to build and train machine learning models using a Jupyter notebook instance.

Sources:
sagemaker_documentation/deeplens-getting-started-launch-sagemaker.md
sagemaker_documentation/integrating-sagemaker.md
sagemaker_documentation/sagemaker-marketplace.md
```

### Important
Ensure that the Hugging Face API key is kept secure and not shared publicly (in this specific case, the API key is being shown only to the users with reading permissions in this private repository).
Some parts of the code are commented out for optional features (e.g., loading vector database from disk).
