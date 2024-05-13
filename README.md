# Peirpl Singh for TestLine

This repository contains a machine learning model that enables chat with a PDF document. (I know that was not the original assignment, however it is the best I could have come up with, trust me I am learning)

The model utilizes language processing techniques to extract information and answer questions based on the content of the PDF.

## Installation

You can install the necessary dependencies using pip:

```bash
!pip install langchain
!pip install langchain_google_cgenai
!pip install ChatGoogleGenerativeAI
!pip install chromadb install 
!pip install pypdf
```

## Usage

1. Import the required modules:

```python
import sys

sys.path.append('/kaggle/input/rag-builder-file')

# now i can import files from my data that have ragebuilder.py and get_api.py
import ragebuilder
import get_api
```

2. Initialize the model and load the PDF document:

```python
api = get_api.get_api()
model = ragebuilder.LangchainGemeni(api, temperature=0.3)

# Convert PDF pages into vectors
model.AIEmbeddingsPdfPages2Vector("Your_PDF_File.pdf")
```

3. Build the Question-Answering system:

```python
# Summon your trusty Question-Answering guardian
qa_client = model.BuildQA(return_source_documents=True)

# Ask questions and get answers
qa_model = qa_client({
    'query': "tell me, is the person mentioned a Kaggle master?"
})

print(qa_model['result'])

qa_model = qa_client({
    'query': "what programming languages are mentioned?"
})

print(qa_model['result'])
```

## Example

```python
# Ask questions and get answers
qa_model = qa_client({
    'query': "tell me, is the person mentioned a Kaggle master?"
})

print(qa_model['result'])

qa_model = qa_client({
    'query': "what programming languages are mentioned?"
})

print(qa_model['result'])
```

## Contributors

- [Pritpal Singh](https://github.com/pritpalcodes)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
