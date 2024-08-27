# Episode-5
Episode 5: Finding Relationship with a Knowledge Graph

*TL;DR The objective of this episode is to upload data to a Neo4j Aura instance. We'll be using the Hugging Face API with the Inference Client to get responses from the Mixtral Foundation Model, which will help us analyze financial news data obtained from the Marketaux API.*

# Introduction

The are a lot of survey paper explaining that propietary model such as GPT 4.0 and Claude 3 are surpassing capabilities from open source model like LLaMa, Falcon, Mistral, etc. The reality is that there is a ranking for that. But what happen if we dont have any money? Just a computer, a colab notebook and our brain. In December of 2023 Mistral AI came up with a LLM overpassing on benchamark models like GPT3.5 and LLaMa 2 70B, Mixtral 8x7B Instruct to featuring text extraction. In this episode we are going to use Mixtral to extract key words, summary to create relationships and entities on a database Neo4j. Using the Hugging Face API with the Inference Client that allow us to interact directly with Mixtral without downloading any model in our computer, doing this, we are going to obtain a concept called Knowledge Graph that is allowing to find relationship between objects in this case; Financial News from NVIDIA coming from the Marketaux API a financial news API and the best part of each tool that we are using is that eversingle one of them are free to use or has a free tier on it.

## Data Extraction from Marketaux API
This image illustrates the process of extracting financial news articles using the Marketaux API. The workflow begins with the API retrieving 99 pages of news, amounting to a total of 297 articles. All of this data is then consolidated into a single JSON file. From this file, each news article is extracted separately, including only key elements such as the title, description, published date, and highlights. These individual pieces of information are then stored as unique documents, each representing a financial news item ready for further analysis.


![Diagrama en blanco - Página 1 (2)](https://github.com/user-attachments/assets/cf731986-3e10-40b2-8e0e-9006303a2eba)

## Hugging Face API and Mixtral
1. **Set Up the API Client**: First, you need to connect to the Hugging Face API using a special tool called the Inference Client. This client allows you to interact with Mixtral without having to download or run the model on your own machine.
2. **Prepare Your Message**: Before sending your message to Mixtral, you need to structure it properly. This involves creating a "system message" in this case this is our variable systeam_msg that sets the context as a financial analyst expert in extract information from financial news and a "user message" that contains the specific content or question you want the model to respond to in this case file_prompt is our variable containing the prompt engineering template and the financial news.
3. **Send the Message**: With your message ready, you send it to Mixtral through the API. The model processes your input and starts generating a response. Depending on your setup, the response can be streamed back to you in chunks, allowing you to see the answer as it’s being formed.
4. **Receive the Response**: The response from Mixtral is received in the form of text, which you can print out or further process. Since the response is streamed, you might collect it piece by piece and then combine it into a complete answer.
Use the Response: Once you have the full response, you can use it in your application. For instance, you might extract keywords, summarize the content, or identify relationships within the data, depending on what you need for your project.

## Prompt Engineering
Using Few-Shot Prompting, we guide the model by providing an example JSON with entities, labels, and IDs. For instance, if we need the model to identify financial entities in news articles, we might provide a few examples such as “Company: NVIDIA” and “Product: GPU.” Similarly, when dealing with relationships, we might include examples like “NVIDIA acquired Mellanox Technologies” and specify the relationship types such as acquisition. This way, the model learns from the given examples and applies the same structure to new, unseen data.

For In-Context Learning, I applied it to relationships by explaining what the relationship should be and giving an example. For example, if we want to extract investment relationships, we might say, “The company invested in another company,” followed by an example like “NVIDIA invested in ARM.” For entities, I instructed the model on how to construct the summary and where to find the necessary information. For instance, if the goal is to summarize a news article, we might guide the model with instructions such as, “Summarize the key points related to company performance and its impact on stock prices,” and provide an example summary for reference.

The importance of prompt engineering lies in its ability to precisely direct LLMs towards generating relevant and accurate outputs, which is crucial for achieving desired results and maintaining consistency in data extraction and analysis.

The approach I'm using is based on a paper titled: [FinDKG: Dynamic Knowledge Graphs with Large Language Models for Detecting Global Trends in Financial Markets](https://arxiv.org/pdf/2407.10909)
