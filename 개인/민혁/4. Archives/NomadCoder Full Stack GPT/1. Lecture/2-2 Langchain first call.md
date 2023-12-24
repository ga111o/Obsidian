```
from langchain.llms.openai import OpenAI
from langchain.chat_models import ChatOpenAI, ChatOllama
```

in my case, i dont use openai
only use ollama in localstorage

```
llm = OpenAI()
# chat = ChatOpenAI()
chat = ChatOllama(
    model = "mistral:latest",
)

# a = llm.predict("what is linux")
b = chat.predict("what is linux?")

b
```

<br>

1. call `Ollama` use `langchain.chat_models`
2. and just print that

<br>
need to study langchain's func

<hr>
<br>

if running ollama, can access 'http://localhost:11434/'

and it return `Ollama is running`
