## Inspiration
**REST API Crash Course – Introduction + Full Python API Tutorial**

---

## What is an API, and why are they “REST-ing”?

An **Application Programming Interface (API)** is a set of rules that allows different pieces of software to communicate with each other. For example, if we have one application written in Python and another written in JavaScript, an API allows those two programs to exchange data and functionality.

A **REST API** is an API that follows a stricter set of conventions. REST stands for **Representational State Transfer** and refers to a subset of APIs that expose predictable URLs and use standard HTTP methods—`GET`, `POST`, `PUT`, and `DELETE`—to interact with resources.

I’ll leave you to figure out `GET`, `POST`, and `DELETE`, but here’s a helpful intuition for `PUT`:

> You can think of `PUT` as “re-placing” data. Unlike `POST`, which typically creates something new, `PUT` updates or replaces existing data at a known location.

If you’re curious about the nuance, this Stack Overflow thread is a great reference:  
**What is the difference between POST and PUT in HTTP?**

---

## Why use a REST API?

### 1. Security and abstraction
Let’s say we have a web server with a large amount of private data. Without a REST API, that data could be exposed directly through rendered HTML and client-side inspection. A REST API adds an abstraction layer, exposing only the endpoints we explicitly allow users to interact with, while keeping internal data and logic protected.

### 2. Separation of concerns (front end vs back end)
REST APIs allow front-end and back-end systems to be developed independently. The backend focuses on data and business logic, while the frontend focuses on user experience, with the API acting as a clean contract between the two.

### 3. Reusability
A single REST API can be reused across multiple clients—web apps, mobile apps, internal tools—without duplicating or rewriting backend logic.

---

## Useful (and less obvious) APIs

Many companies and individuals build APIs specifically so others can create tools and applications on top of them.

- **Yahoo Finance API** – Market and financial data  
- **Words API** – Definitions, synonyms, word relationships  
- **OpenAI API** – Language, reasoning, and generative models  

---

## The Project and the Practical
(Coming soon.)
