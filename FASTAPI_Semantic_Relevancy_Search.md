## Inspired From - **[REST API Crash Course Caleb Curry?](https://www.youtube.com/watch?v=qbLc5a9jdXo)**

---

## What aare APIs, and why are they “REST-ing”?

An **Application Programming Interface (API)** is a set of rules that allows different pieces of software to communicate with each other. For example, if we have one application written in Python and another written in JavaScript, an API allows those two programs to communicate.

A **REST API** is an API that follows a stricter set of conventions. REST stands for **Representational State Transfer** and refers to a subset of APIs that expose predictable URLs and use standard HTTP methods—`GET`, `POST`, `PUT`, and `DELETE`—to interact with resources.

I’ll leave you to figure out GET, POST, and DELETE, but will lend you a helpful tip on PUT: 
> You are PUT-ing like a POST, but instead of POST-ing, you are re-PUT-ing information in place of which you are POST-ing or double PUT-ing.
> On second thought, I’ll let you piece things together: [What is the difference between POST and PUT in HTTP?](https://stackoverflow.com/questions/630453/what-is-the-difference-between-post-and-put-in-http)

---

## Why use a REST API?

### 1. Security and abstraction
Let’s say we have a webserver with a bunch of data. 
If we didn’t use a REST API, we would be hosting our private data on a webserver directly (exposed via direct inspection of HTML).  Using an API exposes only the endpoints we want our users to interact with. 

### 2. Separation of Powers (front end vs back end)
REST APIs allow front-end and back-end systems to be developed independently. 

### 3. Reusability
A single REST API can be reused across multiple clients (web apps, mobile apps, internal tools), without duplicating or rewriting backend logic.

---

## Use APIs

Many companies and individuals build APIs specifically so others can create tools and applications on top of them.

- **Yahoo Finance API** – Market and financial data  
- **Words API** – Definitions, synonyms, word relationships  
- **OpenAI API** – We are approaching the singularity. 

---

## The Project and the Practical
(Coming soon.)
