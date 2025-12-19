# Sensors, Semantic Relevancy, and APIs

**12/19/2025, Written By Ian Wells**

This project uses APIs and semantic relevancy to connect an engineer’s application description to relevant website URLs.

![Semantic Relevancy](https://github.com/user-attachments/assets/32286f80-94b8-4cc1-849e-4939face4365)

---

## Focus
- **Semantic Relevancy Search, Cosine Similarity**
- **FastAPI, Python, Gradio**

---

## Background
FUTEK manufactures load cells, torque sensors, and pressure sensors to enable precision measurement through configuration of [Strain Gauge's](https://en.wikipedia.org/wiki/Strain_gauge).

There are hundreds of sensing applications. Engineers can use sensors for test and measurement, quality control, force feedback, automation, robotics….the list goes on.  

To lend perspective on what Is possible, FUTEK provides ~250 [application landing pages](https://www.futek.com/applications). From an SEO perspective, these are accessible via Google, Safari, even Bing. On FUTEK’s website however, navigating through hundreds of applications is not possible via the current internal search (planned for future development). 

Let’s design a search tool to change that.

---

## System Design
- **Customer input:** a short description of their application (ie: Laparoscopic Gripper, Robotics, Space Rated Load Cells, etc…)  
- **Application page data:** the 250+ application titles, notes, and URLs stored in JSON  
- **Relevance Algorithm:** based on the provided application description, we design an algorithm to output the top K most relevant URLs to our input query  
- **An API:** to allow communication between an end user and our backend (making it easy for a web dev team to implement the search tool, [*winking face emoji*] in case you want to implement this @FUTEK_Web_Team).

<p align="center">
  <img width="440" height="337" alt="image" src="https://github.com/user-attachments/assets/48fc9585-c50c-4c4c-8ae8-1ba424dcd124" />
</p>

## Semantic Search

**How does this make you feel?**  
*You are not good enough.*  

**And this, how do you feel after reading this?**  
*Try harder.* 

Both phrases make me feel inadequate, with the silver lining being that each phrase is **semantically similar**.  

A pretrained embedding model expresses its feelings in **vectors**. Specifically, passing the string **“You are not good enough.”** through an embedding model will output a **multi-dimensional vector** (fancy for a really long list of numbers).  

If we do the same for **“Try Harder”** and compare these vectors mathematically, we can assign relevancy or **“how close”** the phrases are in meaning.  

---

### Design of Semantic Algorithm

1. **Use an embedding model** (pretrained language model) to store a semantic vector for each application title that FUTEK has on their website.  We are using all-MiniLM-L6-v2 from Sentence Transformers, a lightweight and free to download model. 
2. **During the application run**, have a user input text and embed this as a query vector.  
3. **Looping through all application vectors** (O(N) time complexity), perform a cosine similarity between query and application vectors, store the comparisons as scores.  
   - **Cosine similarity – Wikipedia**, in our case, is the dot product of two embeddings, under the assumption each vector is normalized (unit length has a magnitude of 1).  
4. **Sort these comparisons by score**, output the top results to see the best matches.  

By the way, **you are good enough**.  

### The Code

**First, let's embed the application titles.**

```python
from sentence_transformers import SentenceTransformer
import json

#Load Our Embedding Model
model = SentenceTransformer("all-MiniLM-L6-v2")

#Load our website application data
with open("results.json", "r", encoding="utf-8") as f:
    data = json.load(f)

#Grab the titles from each website application card
titles = [item["title"] for item in data]

#Embed all titles, and normalize each vector
title_embeddings = model.encode(
    titles,
    normalize_embeddings=True,
    show_progress_bar=True
)

results_with_embeddings = []

#Loop through all the data and embeddings, zip them up and append to results
for item, emb in zip(data, title_embeddings):
    results_with_embeddings.append({
        "title": item["title"],
        "url": item["url"],
        "embedding": emb.tolist()  # convert numpy → JSON-safe
    })

#Dump to JSON
with open("futek_title_embeddings.json", "w", encoding="utf-8") as f:
    json.dump(results_with_embeddings, f, indent=2)
```

**Semantic Comparison Algorithm**

```python
def match_application(application_title: str, top_k: int = 5):
    records = app.state.embedding_records
    embeddings = app.state.embeddings    

    top_k = min(top_k, len(records))

    query_embedding = model.encode(
        application_title,
        normalize_embeddings=True
    )

    scores = embeddings @ query_embedding
    top_idx = scores.argsort()[-top_k:][::-1]

    results = []
    for i in top_idx:
        results.append({
            "matched_title": records[i]["title"],
            "url": records[i].get("url"),
            "score": float(scores[i])
        })

    return results
```

---

**IMAGES w/ Comments**

---

## API Design

We are using **FASTApi** to design a connection between our text input and backend semantic search.

**IMAGES w/ Comments on the Code**

---

Thanks for reading 😊  

If you’d like to learn more or design your own semantic search tool, take a look at the repo for this project. 
