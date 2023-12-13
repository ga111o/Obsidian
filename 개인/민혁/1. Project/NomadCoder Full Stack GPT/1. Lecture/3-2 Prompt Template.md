## Prompt Template

> github repo: **97bbdd7cc4e732e714ef64dd663e992b37d89c71**

`template.format()` return `string`

```python
template = PromptTemplate.from_template("what is different of {hardware1} and {hardware2}")

template.format(hardware1 = "memory", hardware2 = "SSD")
```

return `'what is different of memory and SSD'
`

---

```python
from langchain.prompts import PromptTemplate, ChatPromptTemplate

template = PromptTemplate.from_template("what is different of {hardware1} and {hardware2}")
prompt = template.format(hardware1 = "memory", hardware2 = "SSD")


chat = ChatOllama(
    model = "mistral:latest",
    temperature=0.1,
)
```

```
chat.predict(prompt)
```

return `"\nMemory and SSD  ... SKIP ... programs and opening files."`

func

-   `PromptTemplate`: creating templates from just string
-   `ChatPromptTemplate`: creating templates from message
-   `from_template`: Load a prompt template from a template.
-   `format`: prompt with the inputs.

<br><br>
var

-   `chat`: select model and detail

<br><hr><br>

```python
from langchain.prompts import  ChatPromptTemplate

messages =  ChatPromptTemplate.from_messages([
    ("system", "you are a Korean Computer Science expert. and you must only reply korean")
    ("ai","안녕하세요.제 이름은 {ai_name}입니다."),
    ("human","what is different of {hardware1} and {hardware2}")
])
```

**setting HumanMessage, AIMessage, SystemMessage is super important**

`from_messages` is func. so need to `()`

<br>
<hr>
<br>

```python
template.format_messages()
```

return `KeyError: 'ai_name'`<br>
need to input all arguments
<br>

```
template.format_messages(ai_name = "ga111o", hardware1 = "cpu", hardware2 = "gpu")
```

like this

<br><br>

```python
prompt = template.format_messages(ai_name = "ga111o", hardware1 = "cpu", hardware2 = "gpu")

chat.predict_messages(prompt)
```

return `AIMessage(content='\nCPU (Central Processing Unit) 및 GPU (Graphics Processing Unit)는 컴퓨터의 ... SKIP ... 프로세스러입니다.')`

<br>
<hr>
<br>

![](https://velog.velcdn.com/images/ga111o/post/c4e1bcfa-6486-4aa8-8bf4-a458e59a89c0/image.png)

wow
