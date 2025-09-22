# LangChain/LangGraph v1.0

```python
from langchain.agents import create_agent
from langchain_core.messages import HumanMessage
from pydantic import BaseModel

class Weather(BaseModel):
    temperature: float
    condition: str

def weather_tool(city: str) -> str:
    """Get the weather for a city."""
    return f"it's sunny and 70 degrees in {city}"

agent = create_agent(
    "bedrock:anthropic.claude-3-5-sonnet-20241022-v2:0",
    tools=[weather_tool],
    response_format=Weather
)
result = agent.invoke({"messages": [HumanMessage("What's the weather in SF?")]})
print(repr(result["structured_response"]))
```

이때의 결과는 아래와 같습니다.

```python
python test.py 
Weather(temperature=70.0, condition='sunny')
```

## Agent

[ReAct loop[(https://docs.langchain.com/oss/python/langchain/agents)는 아래와 같습니다.

<img width="324" height="363" alt="image" src="https://github.com/user-attachments/assets/ffed78c7-13dd-4b26-bea2-6ce984173f97" />


## Reference 

[LangChain Python v1.0](https://docs.langchain.com/oss/python/releases/langchain-v1)

[https://docs.langchain.com/oss/python/releases/langchain-v1]

