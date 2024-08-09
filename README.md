# Structured Output with Multimodal Agents in LangGraph

This notebook demonstrates how to create a multimodal agent system using LangGraph to process images and generate structured output. The system extracts data from images and uses it to create poems but you can easily adapt it to other tasks.

## Table of Contents

1. [Overview](#overview)
2. [Why Structured Output is Revolutionary](#why-structured-output-is-revolutionary)
3. [The Cool Factor: Multimodal Agent Integration](#the-cool-factor-multimodal-agent-integration)
4. [Prerequisites](#prerequisites)
5. [Installation](#installation)
6. [Usage](#usage)
7. [Workflow](#workflow)
8. [Components](#components)
9. [Scaling](#scaling)
10. [Notes](#notes)

## Overview

I'm excited to share insights from my latest project on "Structured Output with Multimodal Agents," a notebook that showcases the incredible potential of structured data and the intelligent routing of tasks to various large language models (LLMs).

### Why Structured Output is Super Helpful

Structured output is a cornerstone of effective automation. It transforms raw data into organized, easily interpretable formats, enabling seamless integration across different stages of an automation pipeline. This consistency ensures that automation scripts can reliably process information, reducing errors and boosting efficiency.

Moreover, structured output can provide 'space' for additional processing and analysis, enabling more sophisticated AI models areas for planning, reasoning, and decision-making. This can be crucial for complex tasks that require multi-step processing and integration of diverse data sources.

### Multi-LLM and Multimodal Integration

This notebook exemplifies the next level of AI integration by routing tasks to specialized LLMs. Here's how it works:

1. **Claude 3 Haiku**: This model handles the initial image processing. It extracts key data points from images, such as colors, text, objects, and even subjective elements like "vibes." This structured data forms the basis for subsequent processing.

2. **Task Routing and State Management**: The extracted image data is stored in the agent's state, creating a comprehensive dataset that encapsulates all relevant aspects of the image.

3. **LLAMA 70B via Groq's Function Calling**: Leveraging Groq's function calling, this model uses the structured data to generate a haiku. It not only produces the poem but also provides a detailed explanation of the reasoning behind it.

### Why This Approach is Exciting

This approach highlights the synergy between different AI models, each contributing its unique strengths to achieve a cohesive outcome. By assigning tasks to the most suitable LLM, we optimize performance and accuracy, pushing the boundaries of what AI can accomplish.

The result is a rich, multi-faceted output: all extracted data points from the image, the generated haiku, and the reasoning behind the poem. This demonstrates the powerful capabilities of modern AI to handle complex, multimodal tasks with elegance and precision.

## Prerequisites

- Python 3.x
- API keys for Groq and Anthropic

## Installation

1. Clone this repository or download the notebook.

2. Install the required libraries:

```bash
pip install langchain langchain-groq langgraph langchain-anthropic
```

3. Set up your environment variables:
   - GROQ_API_KEY
   - ANTHROPIC_API_KEY

   Optionally, you can set up LangSmith tracing by uncommenting and setting the relevant environment variables in the notebook.

## Usage

1. Open the notebook in a Jupyter environment.
2. Run each cell in order, following the instructions provided.
3. When prompted, enter your API keys for Groq and Anthropic.
4. The notebook will guide you through the process of setting up the multimodal agent system and testing it on sample images.

## Workflow

The workflow consists of two main steps:

1. **Data Extraction**: The system uses Claude 3 Haiku to extract structured data from the input image, including colors, text, objects, and vibes.
2. **Poem Generation**: Using the extracted data, the system employs LLAMA 70B via Groq's function calling to generate a haiku poem along with the reasoning behind it.

## Components

### Objects

- `ImageDataPoints`: A Pydantic model for storing structured data extracted from images.
- `AgentReasoning`: A Pydantic model for storing the reasoning and final answer of the poem generation step.
- `AgentState`: A TypedDict for maintaining the state of the agent throughout the workflow.

### Functions

- `encode_image`: A helper function to encode images to base64 format.
- `extract_data`: Extracts structured data from the input image using Claude 3 Haiku.
- `generate_poem`: Generates a haiku poem based on the extracted data using LLAMA 70B via Groq's function calling.

### LangGraph Workflow

The notebook sets up a LangGraph workflow with two nodes:
1. "extract_data"
2. "generate_poem"

The workflow is compiled into a LangChain Runnable, allowing for easy execution and integration with other LangChain components.

## Scaling

The notebook includes a section demonstrating how to scale the system to process multiple images. It iterates through all images in a specified directory, applying the workflow to each one.

## Notes

- The notebook uses structured output capabilities of the AI models to ensure consistent and parseable responses.
- The system is designed to be modular, allowing for easy extension or modification of individual components.
- Error handling and edge cases are not extensively covered in this demo notebook. In a production environment, you would want to add more robust error handling and input validation.
- The performance and output quality may vary depending on the specific images used and the current capabilities of the AI models employed.