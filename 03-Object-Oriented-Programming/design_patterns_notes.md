# Design Patterns Notes

## 1. Factory Method
**Context:** LangChain related class understanding

### Concept
The Factory Method pattern provides an interface for creating objects in a superclass, but allows subclasses to alter the type of objects that will be created. It's about **deferring instantiation to subclasses**.

### Intuitive Example: The "Pizza Store"
Imagine a Pizza Store. You have a base `PizzaStore` class with a `create_pizza()` method.
- `NYStylePizzaStore` subclass implements `create_pizza()` to return NY-style pizzas (thin crust).
- `ChicagoStylePizzaStore` subclass implements `create_pizza()` to return Chicago-style pizzas (deep dish).
The client code (ordering a pizza) doesn't need to know the specific class of pizza, just that it's getting a pizza.

### LangChain Application
In LangChain, this is often seen when initializing different types of LLMs or Agents based on configuration.

```python
from abc import ABC, abstractmethod
from langchain_openai import ChatOpenAI
from langchain_anthropic import ChatAnthropic

class LLMFactory(ABC):
    @abstractmethod
    def create_llm(self):
        pass

class OpenAIFactory(LLMFactory):
    def create_llm(self):
        return ChatOpenAI(model="gpt-4")

class AnthropicFactory(LLMFactory):
    def create_llm(self):
        return ChatAnthropic(model="claude-3-sonnet")

# Client code
def get_response(factory: LLMFactory, prompt: str):
    llm = factory.create_llm() # The "Factory Method" call
    return llm.invoke(prompt)
```

---

## 2. Abstract Factory
**Context:** Creating LLM application related classes specially with LangChain class understanding

### Concept
The Abstract Factory pattern lets you produce families of related objects without specifying their concrete classes. It's a **factory of factories**.

### Intuitive Example: The "Furniture Factory"
You need to furnish a room. You have an `AbstractFurnitureFactory` with methods `create_chair()` and `create_sofa()`.
- `ModernFurnitureFactory` creates `ModernChair` and `ModernSofa`.
- `VictorianFurnitureFactory` creates `VictorianChair` and `VictorianSofa`.
You ensure that your chair and sofa match because they come from the same factory.

### LLM Application Context
In a complex LLM app, you might need a "family" of components that work together: an LLM, a specific Prompt Template, and a Parser.

```python
class AIProviderFactory(ABC):
    @abstractmethod
    def create_llm(self): pass
    
    @abstractmethod
    def create_prompt_template(self): pass

class OpenAIProvider(AIProviderFactory):
    def create_llm(self):
        return ChatOpenAI()
    
    def create_prompt_template(self):
        # OpenAI specific prompting strategies
        return ChatPromptTemplate.from_messages(...)

class LocalLlamaProvider(AIProviderFactory):
    def create_llm(self):
        return Ollama(model="llama3")
    
    def create_prompt_template(self):
        # Llama specific prompting (e.g. specific system tokens)
        return PromptTemplate.from_template(...)

# Usage
def configure_app(provider: AIProviderFactory):
    llm = provider.create_llm()
    prompt = provider.create_prompt_template()
    # These are guaranteed to be compatible
    return prompt | llm
```

---

## 3. Decorator
**Context:** Timer and Logger

### Concept
The Decorator pattern allows you to attach new behaviors to objects (or functions) by placing these objects inside special wrapper objects that contain the behaviors.

### Intuitive Example: The "Coffee Shop"
You start with a basic `Coffee`.
- You wrap it in a `MilkDecorator` -> Coffee with Milk.
- You wrap that in a `SugarDecorator` -> Coffee with Milk and Sugar.
The base object is still a coffee, but it has added "features".

### Python Application (Timer & Logger)
In Python, decorators are a native syntax (`@decorator`) used extensively for cross-cutting concerns like logging and timing.

```python
import time
import functools
import logging

# Setup logger
logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def timer_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        execution_time = end_time - start_time
        logger.info(f"Function {func.__name__} took {execution_time:.4f} seconds")
        return result
    return wrapper

def log_decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        logger.info(f"Calling {func.__name__} with args={args} kwargs={kwargs}")
        try:
            result = func(*args, **kwargs)
            logger.info(f"{func.__name__} returned {result}")
            return result
        except Exception as e:
            logger.error(f"{func.__name__} failed with error: {e}")
            raise
    return wrapper

# Usage in LLM App
@log_decorator
@timer_decorator
def generate_summary(text: str):
    # Simulate LLM call
    time.sleep(1) 
    return f"Summary of: {text[:10]}..."

generate_summary("Long article text here")
```

---

## 4. Iterator
**Context:** Building data structures, and understand how loop works in python

### Concept
The Iterator pattern lets you traverse elements of a collection without exposing its underlying representation (list, stack, tree, etc.).

### Intuitive Example: The "MP3 Player"
You have a playlist. You can press "Next" to get the next song. You don't care if the songs are stored in an array, a linked list, or a tree structure internally. You just want the next song.

### Python Internals (How loops work)
Python's `for` loop is syntactic sugar for the Iterator protocol.

**The Protocol:**
1.  **Iterable**: An object that has an `__iter__` method which returns an **Iterator**.
2.  **Iterator**: An object that has a `__next__` method which returns the next item or raises `StopIteration` when done.

**Simulating a `for` loop with `while`:**

```python
# Standard for loop
colors = ["red", "green", "blue"]
for color in colors:
    print(color)

# What actually happens (The Iterator Pattern)
print("--- Internal Working ---")
iterator = iter(colors) # Calls colors.__iter__()

while True:
    try:
        color = next(iterator) # Calls iterator.__next__()
        print(color)
    except StopIteration:
        break # Loop ends
```

---

## 5. State
**Context:** How LangGraph internal works

### Concept
The State pattern allows an object to alter its behavior when its internal state changes. The object will appear to change its class.

### Intuitive Example: The "Vending Machine"
- **State: NoCoin** -> If you press "Buy", nothing happens.
- **State: HasCoin** -> If you press "Buy", it dispenses item and switches to "NoCoin".
- **State: SoldOut** -> If you insert coin, it rejects it.
The machine behaves differently depending on its current state.

### LangGraph Internals
LangGraph uses a **State Graph** where the "State" is a shared data structure (schema) that is passed between nodes.

1.  **The State Schema**: Defines the structure of data (e.g., `TypedDict` with `messages` list).
2.  **Nodes**: Functions that receive the current state, perform work (e.g., call LLM), and return a *state update*.
3.  **Edges**: Logic that determines the next node based on the current state.

```python
from typing import TypedDict, Annotated
from langgraph.graph import StateGraph, END

# 1. Define State
class AgentState(TypedDict):
    messages: list[str]
    current_step: str

# 2. Define Nodes (Transitions)
def chatbot(state: AgentState):
    # Behavior depends on state (history)
    new_msg = "AI Response based on " + state['messages'][-1]
    return {"messages": [new_msg], "current_step": "respond"}

def tool_executor(state: AgentState):
    # Executes if state indicates tool usage needed
    return {"messages": ["Tool Result"], "current_step": "tool_done"}

# 3. Build Graph
workflow = StateGraph(AgentState)
workflow.add_node("chatbot", chatbot)
workflow.add_node("tool_executor", tool_executor)
# ... edges define the state machine flow
```

---

## 6. Template Method
**Context:** Document extractor type for the LLM application

### Concept
The Template Method defines the skeleton of an algorithm in the superclass but lets subclasses override specific steps of the algorithm without changing its structure.

### Intuitive Example: The "Beverage Maker"
Base class `CaffeineBeverage` has a method `prepare_recipe()`:
1.  Boil Water
2.  `brew()` (Abstract)
3.  Pour in cup
4.  `add_condiments()` (Abstract)

- `Tea` subclass implements `brew()` (steep tea bag) and `add_condiments()` (lemon).
- `Coffee` subclass implements `brew()` (drip coffee) and `add_condiments()` (sugar/milk).
The overall process (boil -> brew -> pour -> condiments) is the same (the template).

### LLM Document Extractor Application
In a document processing pipeline, the overall flow is often consistent, but the specifics change per document type.

```python
from abc import ABC, abstractmethod

class DocumentExtractor(ABC):
    # The Template Method
    def extract(self, file_path: str):
        text = self.load_file(file_path)
        clean_text = self.clean_text(text)
        data = self.analyze_with_llm(clean_text)
        return self.format_output(data)

    @abstractmethod
    def load_file(self, path: str) -> str:
        pass

    # Hook method (optional override)
    def clean_text(self, text: str) -> str:
        return text.strip()

    @abstractmethod
    def analyze_with_llm(self, text: str) -> dict:
        pass
    
    def format_output(self, data: dict) -> dict:
        return {"result": data}

# Concrete Implementation for PDF
class PDFInvoiceExtractor(DocumentExtractor):
    def load_file(self, path: str):
        # Specific PDF loading logic
        return "Loaded PDF Content"
    
    def analyze_with_llm(self, text: str):
        # Specific prompt for Invoices
        return {"total": 100, "date": "2023-01-01"}

# Concrete Implementation for Text
class ResumeExtractor(DocumentExtractor):
    def load_file(self, path: str):
        # Specific Text loading logic
        return "Loaded Resume Content"
    
    def analyze_with_llm(self, text: str):
        # Specific prompt for Resumes
        return {"name": "John Doe", "skills": ["Python", "AI"]}
```
