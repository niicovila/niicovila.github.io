---
layout: page
title: Information Retrieval using Transformer Based Embeddings
description: A search engine of tweets related to the russo-ukranian war using transformer based embeddings
img: assets/img/irwa.png
importance: 5
category: Machine Learning
---
# Information Retrieval System for Tweet Analysis
<a href="https://github.com/niicovila/IRWA_Project">This project</a> is an information retrieval system that we developed to process and rank tweets related to specific queries, with a primary focus on geopolitical events such as the Russia-Ukraine conflict. The system combines traditional information retrieval methods with modern machine-learning techniques to ensure that search results are both accurate and relevant. The project includes various components, ranging from indexing and ranking algorithms to a user interface and web analytics integration.

## Indexing and TF-IDF Computation

Our system begins with the creation of an inverted index for all terms found within a dataset of tweets. We use TF-IDF (Term Frequency-Inverse Document Frequency) values to rank these tweets based on their relevance to specific user queries. This approach allows for efficient retrieval and provides an initial ranking that serves as the foundation for further processing. By employing these traditional methods, we can quickly filter and sort tweets according to their textual relevance.

## Transformer-Based Embedding and Ranking

To enhance the ranking process, we incorporated transformer-based embeddings that capture the semantic meaning of tweets. This advanced method computes the cosine similarity between the embeddings of user queries and those of the tweets, enabling us to rank tweets not just by keyword matching but by their contextual relevance. Additionally, we integrated social metrics such as likes and retweets into our ranking algorithm to further refine the relevance of the results. By doing so, we consider both the semantic content of the tweets and their popularity or importance within the social media ecosystem.

## Query Processing and Evaluation

Our system is capable of handling both baseline and custom queries, providing ranked lists of tweets tailored to specific user needs. We implemented several evaluation metrics, including Mean Average Precision, Mean Reciprocal Rank, precision, recall, and NDCG, to measure the performance and effectiveness of our ranking algorithms. These metrics provide a comprehensive view of how well the system retrieves and ranks relevant tweets.

## Clustering and Visualization

To provide a visual representation of tweet distributions, we used word embeddings in combination with T-SNE (t-distributed Stochastic Neighbor Embedding) clustering techniques. This approach allows us to identify clusters that represent major themes or topics within the tweet dataset. Such visualization aids in understanding the broader content and context of the tweets, making it easier to analyze trends and patterns in social media discussions.

## Interactive Query System

We developed an interactive query system where users can input their queries and receive ranked results. This system also allows users to save the results for further analysis. The interactive nature of the query system makes it adaptable to a variety of user needs, ensuring that the application can serve different types of queries effectively. The user interface was designed with simplicity and efficiency in mind, featuring a straightforward layout and a prominent search bar. Search results are presented in a clean and organized manner, which enhances readability and usability.

## Click Tracking and Analytics

As part of the final phase of our project, we integrated click tracking and analytics to capture detailed insights into user interactions with the search results. This involves recording each click on a search result and capturing associated data such as the query terms, the rank of the clicked document, and the unique identifier for each click event. The analytics dashboard displays key metrics using graphs and visualizations, making the complex data accessible even to users who may not be technically inclined. This feature helps us understand user behavior and preferences, as well as evaluate the effectiveness of our search results.

## Data Collection and Session Management

For data collection, we chose an in-memory storage solution to simplify replication and avoid the complexities of setting up a persistent database. This decision was made to facilitate rapid prototyping and ease of use, recognizing that for real-world applications, a more durable and scalable database solution would be necessary. Session management was implemented to accurately track user interactions, ensuring that each session is uniquely identified and preventing the inflation of user session counts.





