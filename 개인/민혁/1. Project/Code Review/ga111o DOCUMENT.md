## CODE REVIEW

### ga111o DOCUMENT

[VIEW CODE](https://raw.githubusercontent.com/ga111o/fullstack-gpt311/main/lecture/7/pages/01_DOCUMENT.py)

```python
import streamlit as st
from langchain.chat_models import ChatOllama
from langchain.callbacks.base import BaseCallbackHandler
from langchain.document_loaders import UnstructuredFileLoader
from langchain.text_splitter import CharacterTextSplitter
from langchain.embeddings import OllamaEmbeddings, CacheBackedEmbeddings
from langchain.vectorstores import FAISS
from langchain.storage import LocalFileStore
from langchain.prompts import ChatPromptTemplate
from langchain.schema.runnable import RunnablePassthrough, RunnableLambda
```

-   create page using `streamlit`
-   `model`: ollma (llama2:7b)
-   `vectorstore`: FAISS
