`output parser`: transform LLM response

txt to tuple or list or DataBase's format ...

<br>

---

<br>

```
from langchain.schema import BaseOutputParser

#simmular base class
class CommaOutputParser(BaseOutputParser):
    #need to create `parse` method
    def parse(self, text: str):
        items = text.strip().split(",")
        return list(map(str.strip, items))

p = CommaOutputParser()


p.parse("hello, how, are, you")
```

return `['hello', 'how', 'are', 'you']`

> need to create `parse` method

`text`<small>(argument)</small>: input content

<br>

---

<br>

```python
output = chat.predict_messages(prompt)
```

return `AIMessage(con .... SKIP ... ,\n10. black.')
`

<br>

```
class CommaOutputParser(BaseOutputParser):
    def parse(self, text: str):
        items = text.strip().split(",")
        return list(map(str.strip, items))

p = CommaOutputParser()

p.parse(output.content)
```

return `['1. red',
 '2. blue',
 '3. green',
 '4. yellow',
 '5. orange',
 '6. purple',
 '7. pink',
 '8. brown',
 '9. gray',
 '10. black.']
`
