# Episode-5
Episode 5: Finding Relationship with a Knowledge Graph

*TL;DR The objective of this episode is to upload data to a Neo4j Aura instance. We'll be using the Hugging Face API with the Inference Client to get responses from the Mixtral Foundation Model, which will help us analyze financial news data obtained from the Marketaux API.*

# Introduction

The are a lot of survey paper explaining that propietary model such as GPT 4.0 and Claude 3 are surpassing capabilities from open source model like LLaMa, Falcon, Mistral, etc. The reality is that there is a ranking for that. But what happen if we dont have any money? Just a computer, a colab notebook and our brain. In December of 2023 Mistral AI came up with a LLM overpassing on benchamark models like GPT3.5 and LLaMa 2 70B, Mixtral 8x7B Instruct to featuring text extraction. In this episode we are going to use Mixtral to extract key words, summary to create relationships and entities on a database Neo4j. Using the Hugging Face API with the Inference Client that allow us to interact directly with Mixtral without downloading any model in our computer, doing this, we are going to obtain a concept called Knowledge Graph that is allowing to find relationship between objects in this case; Financial News from NVIDIA coming from the Marketaux API a financial news API and the best part of each tool that we are using is that eversingle one of them are free to use or has a free tier on it.
