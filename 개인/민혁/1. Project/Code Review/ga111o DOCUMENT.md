## CODE REVIEW

### ga111o DOCUMENT

![img](https://velog.velcdn.com/images/ga111o/post/994835f8-d647-4bea-b5ec-81b4cafce20d/image.png)

[VIEW ALL CODE](https://raw.githubusercontent.com/ga111o/fullstack-gpt311/main/lecture/7/pages/01_DOCUMENT.py)

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

<br>
<hr>
<br>

```python
class ChatCallbackHandler(BaseCallbackHandler):
    message = ""

    def on_llm_start(self, *args, **kwargs):
        self.message_box = st.empty()

    def on_llm_end(self, *args, **kwargs):
        save_message(self.message, "ai")

    def on_llm_new_token(self, token, *args, **kwargs):
        self.message += token
        self.message_box.markdown(self.message)

```

`ChatCallbackHandler`: class inherit from `BaseCallbackHandler` and overrides three methods(start, end, new_token) to control the display of messages. It seems to capture tokens from the model responses and add them to the display.

<br>
<hr>
<br>

```python
ollama = ChatOllama(
    model = "llama2:7b",
    temperature=0.1,
    streaming=True,
    callbacks=[
        ChatCallbackHandler(),
    ]
)
```

model settings

<br>
<hr>
<br>

```python
@st.cache_data(show_spinner="Embedding file...")
def embed_file(file):
    file_content = file.read()
    file_path = f"./.cache/files/{file.name}"
    with open(file_path, "wb") as f:
        f.write(file_content)
    cache_dir = LocalFileStore(f"./.cache/embedings/{file.name}")
    splitter = CharacterTextSplitter.from_tiktoken_encoder(
        separator="\n",
        chunk_size=600,
        chunk_overlap=100,
    )
    loader = UnstructuredFileLoader(file_path)
    docs = loader.load_and_split(text_splitter=splitter)
    embeddings = OllamaEmbeddings()
    cached_embeddings = CacheBackedEmbeddings.from_bytes_store(embeddings, cache_dir)
    vectorstore = FAISS.from_documents(docs, cached_embeddings)
    retriever = vectorstore.as_retriever()
    return retriever
```

`embed_file`: allowing the caching of embedding file operations.

-   `@st.cache`: decorate emved_file func

1. get file and save at the path
2. split file content and save embeddings path
    - using FAISS(vectorstore), vectorization content.
3. use `as_retriever()`
    - langchain's basic func.

<br>
<hr>
<br>

```python
def save_message(message, role):
    st.session_state["messages"].append({"message": message, "role": role})

def send_message(message, role, save=True):
    with st.chat_message(role):
        st.markdown(message)
    if save:
        st.session_state["messages"].append({"messages": message, "role":role})

def paint_history():
    for message in st.session_state["messages"]:
        send_message(message["messages"], message["role"], save=False)
```

`st.session_state` is dict.<br>
use as a vatiable

<br>
<hr>
<br>

```python
if file:
    retriever = embed_file(file)
    send_message("READY!", "ai", save=False)
    paint_history()
    message = st.chat_input("")
    if message:
        send_message(message, "human")
        chain = (
            {
                "context": retriever | RunnableLambda(format_docs),
                "question": RunnablePassthrough(),
            }
            | template
            | ollama
        )
        with st.chat_message("ai"):
            response = chain.invoke(message)
else:
    st.session_state["messages"]=[]
```

handling file embedding and message exchange.
