# LangGraph Components - Simple Example

This repository contains a simple example of building an agent using LangGraph components. It demonstrates how to create a conversational agent that can search for information and respond to user queries using a state-based workflow.

## Overview

[LangGraph](https://github.com/langchain-ai/langgraph) is a library for building stateful, multi-actor applications with LLMs. This example demonstrates:

- Creating a simple agent using the ReAct (Reasoning + Action) pattern
- Implementing a state-based workflow with LangGraph
- Integrating external tools (Tavily search) with a language model
- Building a travel planning assistant that can search for and provide information

## Prerequisites

- Python 3.8+
- OpenAI API key
- Tavily API key

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/KansSoftware/langlraph-components-simple-example
   cd LangGraph\ Components\ -\ Simple\ Example
   ```

2. Create a virtual environment:
   ```
   python -m venv langraph-simple-agent-venv
   ```

3. Activate the virtual environment:
   - Windows:
     ```
     langraph-simple-agent-venv\Scripts\activate
     ```
   - macOS/Linux:
     ```
     source langraph-simple-agent-venv/bin/activate
     ```

4. Install the required packages:
   ```
   pip install -r requirements.txt
   ```

5. Create a `.env` file in the root directory with your API keys:
   ```
   OPENAI_API_KEY=your-openai-api-key
   TAVILY_API_KEY=your-tavily-api-key
   ```

## Usage

Open the Jupyter notebook `LangGraph Components.ipynb` to see the example in action:

```
jupyter notebook "LangGraph Components.ipynb"
```

The notebook demonstrates:

1. Setting up the environment with API keys
2. Creating a search tool using Tavily
3. Defining an agent state structure
4. Implementing a ReAct pattern agent class
5. Running example queries

## Key Components

### Agent State

The agent uses a typed dictionary to maintain state:

```python
class AgentState(TypedDict):
    messages: Annotated[list[AnyMessage], operator.add]
```

### Agent Class

The `Agent` class implements the ReAct pattern with:

- A language model node for processing messages
- An action node for executing tools
- Conditional edges for decision flow
- Methods for handling tool calls and responses

### Example Queries

The notebook includes examples of:

- Simple factual queries (e.g., "What is the capital of Namibia?")
- Multi-part queries (e.g., "What's the best time to visit Kyoto, Japan?")

## Architecture

The agent follows a graph-based architecture:

1. User query is processed by the language model
2. If information is needed, the model calls the search tool
3. Search results are returned to the model
4. The model formulates a final response

## License

[Include license information here]

## Acknowledgments

- [LangChain](https://github.com/langchain-ai/langchain) for the core components
- [LangGraph](https://github.com/langchain-ai/langgraph) for the graph-based workflow
- [OpenAI](https://openai.com/) for the language models
- [Tavily](https://tavily.com/) for the search API
