# chain

```
chain1 = template | chat | parseFunc()
chain2 = template2 | other_chatModel | parseFunc2()

chain1.invoke({
    "inner_argument":"asdfasdf",
})

chain2.invoke({
    "other_inner_arg": "ga111o!",
})
```

```
all = chain1 | chain2 | outPutParser()
```

input chain1's output at chain2

**chain** is composed `Template`,`Language Model`, `Output Parser`

internally, langchain call `format_messages()`, tehn call `chat.predict()`, then call `parseFunc()`

<br>

<hr>

<br>

### detail example

```python
from langchain.chat_models import ChatOllama
from langchain.prompts import ChatPromptTemplate
from langchain.schema import BaseOutputParser
```

```python
# model

chat = ChatOllama(
    model = "mistral:latest",
    temperature=0.1,
)
```

```python
#parser

class CommaOutputParser(BaseOutputParser):
    def parse(self, text: str):
        items = text.strip().split(",")
        return list(map(str.strip, items))
```

```python
#template

template = ChatPromptTemplate.from_messages([
    ("system", "you are list generator. everything you are asked will be answered with a COMMA SEPARATED list of max {max_itm} in lowercase. do NOT reply else. must be COMMA SEPARATED LIST"),
    ("human", "{question}"),
])
```

```python
chain = template | chat | CommaOutputParser()

chain.invoke({"max_itm": 5, "question": "What are the colour?"})
```
