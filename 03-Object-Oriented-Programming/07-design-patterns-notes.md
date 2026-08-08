# Design Patterns Notes

> Architectural patterns and software templates for building flexible, scalable LLM and Python applications.

---

## 📌 Sequence Navigation

This guide is part of the **Python Object-Oriented Programming (OOP) Series**:

1. [01-oops-part-1-introduction.md](./01-oops-part-1-introduction.md) — Procedural vs. OOP Intro
2. [02-oops-four-pillars.md](./02-oops-four-pillars.md) — The Four Pillars of OOP
3. [03-oops-part-2-zero2hero.md](./03-oops-part-2-zero2hero.md) — OOP Foundations, Methods & Inheritance
4. [04-dunder-methods-getters-setters.md](./04-dunder-methods-getters-setters.md) — Dunder Methods & Getters/Setters
5. [05-oops-part-3-zero2hero.md](./05-oops-part-3-zero2hero.md) — Advanced OOP (Composition, Context Managers, Generators)
6. [06-dataclasses-intuitive-guide.md](./06-dataclasses-intuitive-guide.md) — Dataclasses & Boilerplate Elimination
7. **07-design-patterns-notes.md** 👈 *(Current Document)* — Design Patterns in Python
8. [08-ports-and-adapters-architecture.md](./08-ports-and-adapters-architecture.md) — Ports & Adapters Architecture in Python

---

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

class LLMFactory(ABC):
    @abstractmethod
    def create_llm(self):
        pass

class OpenAIFactory(LLMFactory):
    def create_llm(self):
        # Returns OpenAI Chat instance
        return "ChatOpenAI(model='gpt-4')"

class AnthropicFactory(LLMFactory):
    def create_llm(self):
        # Returns Anthropic Chat instance
        return "ChatAnthropic(model='claude-3-sonnet')"

# Client code
def get_response(factory: LLMFactory, prompt: str):
    llm = factory.create_llm() # The "Factory Method" call
    print(f"Instantiated: {llm}")
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
    def create_llm(self):
        pass

    @abstractmethod
    def create_prompt_template(self):
        pass

class OpenAIAppFactory(AIProviderFactory):
    def create_llm(self):
        return "OpenAI LLM"

    def create_prompt_template(self):
        return "OpenAI Specific Prompt"

class AnthropicAppFactory(AIProviderFactory):
    def create_llm(self):
        return "Anthropic LLM"

    def create_prompt_template(self):
        return "Anthropic Specific Prompt"
```
