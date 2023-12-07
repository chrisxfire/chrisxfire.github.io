---
title: prompt engineering
date: 2023-11-28T00:00:00-06:00
draft: true
weight: 1
---

# Overview
*Prompt engineering* is a field of study of the design and optimization of prompts to deliver consistent and quality completions for a given model.

# Motivation
LLMs have a variety of shortcomings to produce reliable and consistent completions:
- The model responses are stochastic (the same prompt may produce different responses).
- The model can fabricate (previously: hallucinate) responses.
- The model capabilities vary.

# Prompt Construction
## Basic prompt
**Prompt**  
> Oh say can you see  

**Completion**  
> It sounds like you're starting the lyrics to "The Star-Spangled Banner," the national anthem of the United States. The full lyrics are ...

## Complex Prompt
A *complex prompt* adds context and instructions to a basic prompt. In Azure OpenAI, complex prompts are constructed as a collection of *messages* that include:
- Input/output pairs reflecting *user* input and *assistant* response.
- *System* messages that set the context for assistant behavior or personality.

```python
response = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Who won the world series in 2020?"},
        {"role": "assistant", "content": "The Los Angeles Dodgers won the World Series in 2020."},
        {"role": "user", "content": "Where was it played?"}
    ]
)
```

## Instruction Prompt
An *instruction prompt* takes a basic prompt and adds additional instruction to it:  

**Basic prompt**  
> Write a description of the Civil War.  

**Instruction prompt**  
> Write a description of the Civil War. Provide key dates and events and describe their significance

**Instruction prompt**  
> Write a description of the Civil War in 1 paragraph. Provide 3 bullet points with key dates and their significance. Provide 3 more bullet points with key historical figures and their contributions. Return the output as a JSON file.

## Primary Content
In the *primary content* design pattern, the input text is divided into two parts:
- content
- an action

**Prompt (<g>instruction</g>)**  
> Jupiter is the fifth planet from the Sun and the largest in the Solar System. It is a gas giant with a mass one-thousandth that of the Sun, but two-and-a-half times that of all the other planets in the Solar System combined. Jupiter is one of the brightest objects visible to the naked eye in the night sky, and has been known to ancient civilizations since before recorded history. It is named after the Roman god Jupiter.[19] When viewed from Earth, Jupiter can be bright enough for its reflected light to cast visible shadows,[20] and is on average the third-brightest natural object in the night sky after the Moon and Venus.
<g>Summarize this in 2 short sentences.</g>

### *n*-shot Examples
In this approach, primary content is used to "feed the model" some examples of the desired output.

In one-shot learning, the model is given a single input/expected output pair:  

**Prompt**  
> The Sun is Shining => El Sol está brillando.  
It's a Cold and windy Day =>

**Completion**  
> Es un día frío y ventoso

<br /> 
In few-shot learning, several input/expected output pairs are provided:  

**Prompt**  
> The player ran the bases => Baseball  
The player hit an ace => Tennis  
The player hit a six => Cricket  
The player made a slam-dunk =>

### Prompt Cues
In this approach, primary content includes cues after the instruction that start the desired response.

**Prompt (<o>instruction</o>, <g>cue</g>)** 
> Jupiter is the fifth planet from the Sun and the largest in the Solar System. It is a gas giant with a mass one-thousandth that of the Sun, but two-and-a-half times that of all the other planets in the Solar System combined. Jupiter is one of the brightest objects visible to the naked eye in the night sky, and has been known to ancient civilizations since before recorded history.  
<o>Summarize This</o>  
<g>What we learned is that Jupiter</g>  

### Templates
A pre-defined recipe for a prompt that can be stored and reused as needed. It may contain placeholders:

```python
from langchain.prompts import PromptTemplate

prompt_template = PromptTemplate.from_template(
    "Tell me a {adjective} joke about {content}."
)
prompt_template.format(adjective="funny", content="chickens")
```

## Supporting Content
Assume a course catalog with extensive metadata (name, description, level, metadata tags, instructor etc.) on all the available courses in the curriculum:
- The *instruction* may be to *summarize the course catalog for Fall 2023*
- The *primary content* may provide a few examples of the desired output
- The *secondary content* may be used to identify the top 5 "tags" of interest

# Prompt Engineering Best Practices
* **Separating instructions and context.** Some models provide delimiters to distinguish between these.
* **Be specific**. Consider providing details about the desired context, outcome, length, format, and style.
* **Be descriptive**. Start with zero-shot and then try refining with one-shot or few-shot. Provide examples. Use analogies.
* **Use fallbacks**. Give the model a *fallback completion* to reduce chances of the model generating fabricated responses.

# Advanced Prompt Engineering
## Chain-of-thought
**Prompt**  
> Alice has 5 apples, throws 3 apples, gives 2 to Bob and Bob gives one back, how many apples does Alice have?

**Completion**  
> 5

This is incorrect.

Use chain-of-thought prompting to give the LLM a similar example and show how to calculate a response correctly:

**Prompt**  
> Lisa has 7 apples, throws 1 apple, gives 4 apples to Bart and Bart gives one back: 7 -1 = 6 6 -4 = 2 2 +1 = 3  
> Alice has 5 apples, throws 3 apples, gives 2 to Bob and Bob gives one back, how many apples does Alice have?

**Completion**  
> 1

## Self-refinement or Critique
Use these steps:
1. Initial prompt asking the LLM to solve a problem.
2. LLM provides completion.
3. Ask the LLM how it can improve its own completion (self-refinement), or, tell the LLM what is wrong with the completion (critique) and ask it to retry.
4. LLM provides new completion, this time considering the request to self-refine or the critique.

## Maieutic Prompting
Use these steps:
1. Ask the LLM to answer a question
2. For each part of the answer, ask the LLM to explain it more in depth.
3. If there are inconsistencies, discard the parts that are inconsistent.

### Example
**Prompt**  
> How can I create a crisis plan to mitigate a pandemic in 5 steps?

**Completion**  
> 1. Identify the risks
> 2. Identify the stakeholders
> 3. Identify the resources
> 4. Identify the actions
> 5. Identify the communication channels

**Prompt**  
> Explain the first step in more detail, what are the risks in detail with a pandemic?

**Completion**  
> The risks are the following:
> - Loss of life
> - Loss of business
> - Loss of reputation
> - Loss of customers
> - Loss of employees

**Prompt**  
> In a pandemic, which is the biggest risk and why?

**Completion**  
> The biggest risk is loss of life because it's the most important thing to protect.

**Prompt**  
> What are the two biggest risks in a pandemic?

**Completion**  
> The two biggest risks are loss of life and loss of business.

We now have confidence that the LLM is consistent regarding Step 1.