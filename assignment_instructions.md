# Multimodal Search Engine Demo

This project takes the concepts of embeddings, RAG, and multimodality that were discussed in the previous course and combines them into a single, impressive prototype. The goal is to build a search engine that can find a picture based on a text query, or find text based on an image query.

**Data:** Either Flickr8k, or a dataset of your choice

## Concrete Instructions:

### Part 1: Data Preparation & Embedding 
1. Load the provided dataset into your Jupyter Notebook.
2. Choose a pre-trained multimodal model from Hugging Face that can handle both images and text.
3. Write a script to iterate through the dataset, process each item, and generate vector embeddings. Store the embeddings along with their corresponding text and image filename.

### Part 2: Search Functionality
1. Implement a search function that takes a text query as input.
2. Embed the text query using your chosen model.
3. Calculate the cosine similarity between the query embedding and all the stored image embeddings.
4. Return and display the top 5 most similar images to the text query.
5. Write a brief analysis of why you think the model returned those images.

### Part 3: Multimodal & Interface Upgrade (Advanced continuation)
1. Extend your search function to handle image queries. This means a user can upload an image, and your system will return the most similar text descriptions.
2. Develop a simple web application using Streamlit or Gradio. This application should have two main functions: a text input field for text-to-image search and an image upload field for image-to-text search.
3. Include a brief description of the project and the technology used in the app itself.
