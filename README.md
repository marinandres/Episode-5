# Episode-5
Episode 5: Finding Relationship with a Knowledge Graph

*TL;DR The objective of this episode is to upload data to a Neo4j Aura instance. We'll be using the Hugging Face API with the Inference Client to get responses from the Mixtral Foundation Model, which will help us analyze financial news data obtained from the Marketaux API.*

# Introduction

The are a lot of survey paper explaining that propietary model such as GPT 4.0 and Claude 3 are surpassing capabilities from open source model like LLaMa, Falcon, Mistral, etc. The reality is that there is a ranking for that. But what happen if we dont have any money? Just a computer, a colab notebook and our brain. In December of 2023 Mistral AI came up with a LLM overpassing on benchamark models like GPT3.5 and LLaMa 2 70B, Mixtral 8x7B Instruct to featuring text extraction. In this episode we are going to use Mixtral to extract key words, summary to create relationships and entities on a database Neo4j. Using the Hugging Face API with the Inference Client that allow us to interact directly with Mixtral without downloading any model in our computer, doing this, we are going to obtain a concept called Knowledge Graph that is allowing to find relationship between objects in this case; Financial News from NVIDIA coming from the Marketaux API a financial news API and the best part of each tool that we are using is that eversingle one of them are free to use or has a free tier on it.

## Data Extraction from Marketaux API
This image illustrates the process of extracting financial news articles using the Marketaux API. The workflow begins with the API retrieving 99 pages of news, amounting to a total of 297 articles. All of this data is then consolidated into a single JSON file. From this file, each news article is extracted separately, including only key elements such as the title, description, published date, and highlights. These individual pieces of information are then stored as unique documents, each representing a financial news item ready for further analysis.


![Diagrama en blanco - Página 1 (2)](https://github.com/user-attachments/assets/cf731986-3e10-40b2-8e0e-9006303a2eba)
