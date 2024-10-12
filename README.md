## Retrieval Augmented Generation information security consultant system implemented through langchain.
The data is collected through the CustomWebLoader class, whose object accepts a list of references to articles from which data will be retrieved to set the context of the model. 
After parsing the data from the web pages, the data is cleaned from unnecessary HTML tags to extract only important information.
After cleaning, the data is subjected to chunking, each chunk is passed to the embedding model to represent the textual data as embeddings. 
Based on the created embeddings, a vector database is created, where each text chunk is matched with its embedding representation. 
The last step is initialising the LLM, on the basis of which and the vector store created earlier, a langchain is created, the principle of operation of which is as follows:
- the user's query is represented as an embedding
- the most relevant data (text chunks) are searched in the vector store based on the embedding of the query
- the found relevant data are substituted into the query template, where it is specified that the model should use these chunks as context before the response
- the generated query is passed to the model
- the response of the model is given together with links to the used articles
