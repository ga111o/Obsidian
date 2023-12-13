## Prompt Template

`template.format` return -> `string`

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

<br><br>
var

-   `chat`: select model and detail
