# Song Recommendation System Using Text and Numerical Feature Embeddings

### Project Overview

This project implements a sophisticated song recommendation system by combining textual and numerical features to generate high-quality embeddings. The project leverages the nomic-ai/nomic-embed-text-v1.5 model from Hugging Face to create embeddings and stores these in a FAISS which is a vector database and utilized it  for efficient similarity search. 

### Objective

The primary objective is to build a recommendation system that can suggest songs based on both their textual attributes (like artist name and song name) and numerical features (such as energy, liveness,tempo etc). By integrating these features, the system provides accurate and relevant song recommendations using the power of LLM (Large Language Model) without even fine tuning them.

### Data and Features

The dataset comprises various features of songs, including:

- *Textual Features*:
  - artist_name
  - song_name
  
- *Numerical Features*:
  - song_acousticness
  - song_danceability
  - song_duration_ms
  - song_energy
  - song_explicit
  - song_instrumentalness
  - song_key
  - song_liveness
  - song_loudness
  - song_mode
  - song_popularity
  - song_speechiness
  - song_tempo
  - song_valence
  - song_year

### About LLM Model
 The model have MTEB score of 69.39. Nomic-embed-text-v1.5 is an improvement upon Nomic Embed that utilizes Matryoshka Representation Learning which gives developers the flexibility to trade off the embedding size for a negligible reduction in performance. Access the model from [here](https://huggingface.co/nomic-ai/nomic-embed-text-v1.5)
 You can read more about the model from their blog by clicking [here](https://blog.nomic.ai/posts/nomic-embed-matryoshka)

### Methodology

1. *Text Embeddings Generation*:
   The nomic-ai/nomic-embed-text-v1.5 model from Hugging Face which was first quantatized by using the LoRA (Low-Rank Adaptation of Large Language Models) technique. It is employed to generate 768-dimensional embeddings for the textual features. This model is renowned for producing high-quality embeddings that capture the semantic meaning of the text effectively.

2. *Normalization of Numerical Features*:
   Numerical features are normalized to ensure that they are on a comparable scale. This step is crucial for combining these features with the text embeddings.

3. *Combining Features*:
   The normalized numerical features are concatenated with the text embeddings to form a comprehensive feature vector. This combined vector represents each song in a multi-dimensional space, capturing both its textual and numerical attributes.

4. *Indexing with FAISS*:
   The FAISS (Facebook AI Similarity Search) library is utilized to store the combined feature vectors. FAISS is an open-source library that excels in efficient similarity search, making it ideal for handling large datasets and performing fast nearest neighbor searches.

### Benefits and Applications

- *Enhanced Recommendation Accuracy*:
  By incorporating both textual and numerical features, the system provides more nuanced and accurate recommendations. For example, features like song_energy, song_liveness, song_mode, and song_tempo play a significant role in capturing the musical characteristics that affect user preferences.

- *Open-Source Model Advantage*:
  The use of the open-source nomic-ai/nomic-embed-text-v1.5 model ensures that the system benefits from state-of-the-art text embedding techniques without proprietary restrictions. This model's ability to generate quality embeddings contributes to the system's high performance. The use of open source model ensures that we don't need to pay for using the LLM service and the quantalization of model using bits and bytes library helped us to work with such a huge parameter model. 

- *Real-Life Applications*:
  This recommendation system can be employed in various real-life scenarios, such as:
  - *Music Streaming Services*: Providing personalized song recommendations to users based on their listening history and preferences.
  - *Retail*: Suggesting music albums or tracks to customers based on their purchase history and browsing behavior.
  - *Marketing*: Crafting targeted marketing campaigns by understanding the musical tastes of different demographic groups.

### Evaluation

The performance of the recommendation system is evaluated using similarity scores. The system computes the similarity between the query song's embedding and the embeddings stored in the FAISS index. The output includes the most similar songs, ranked by their similarity scores. An example of the output is shown below:
![Similarity score output](https://github.com/Mayank-iitp/SpotifyRecommendationSystemusingLLM/assets/151143725/fb25ffc9-c424-40a9-941b-c373263005a7)



### Conclusion

By combining the strengths of the nomic-ai/nomic-embed-text-v1.5 model and the FAISS library, this project demonstrates an effective approach to building a recommendation system that leverages both textual and numerical features. The integration of these features enhances the system's ability to provide accurate and relevant song recommendations, addressing the diverse needs of users in real-life applications.
