# Document-Based Question and Answer System
A question-and-answer system that generates responses based on the documentation provided. 

## Sturcture
![alt text](https://github.com/benaxline/QnA-doc-bot/blob/main/pics/general_system.png)

Above is a basic form of the Q&A system. In the simplest form, we take in documentation and a question which are both sent through the system and generate a response as an output.

![alt text](https://github.com/benaxline/QnA-doc-bot/blob/main/pics/TextSplitterArch.png)

Zooming in, we can see the different components that go into the system. 

## Procedure

#### Splitting
Firstly, we take a PDF file as the documentation. We first split it by page, then further split it into smaller chunks for easier embeddings.

#### Embedding
Next, we need to create embeddings for these chunks of documentation. In this system, we create embeddings with OpenAI's embeddings with [Langchain's OpenAI embedding](https://python.langchain.com/v0.2/docs/integrations/text_embedding/openai/). Langchain allows us to use various embedding and large language models, making it easier to build applications. We send these embeddings to a vector database (here I used Pinecone) to save for future use.

#### Large Language Model
Then, we evaluate the most similar documents from the Pinecone database using the user's query. We take the top chunks of most similar embeddings and pull them from Pinecone. We input the user's query and the most similar embeddings into the large language model. In this system, I used OpenAI's **gpt-4**. This is also from [Langchain](https://python.langchain.com/v0.2/docs/integrations/llms/) as well. 



