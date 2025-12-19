# Sensors, Semantic Relevancy, and APIs

**12/19/2025**

This project uses APIs and semantic relevancy to connect an engineer’s application description to relevant website URLs.

**VISUAL GIF**

---

## Focus
- **Semantic Relevancy Search, Cosine Similarity**
- **FastAPI, Python, Gradio**

---

## Background
FUTEK manufactures load cells, torque sensors, and pressure sensors to enable precision measurement through configuration of [Strain Gauge's](https://en.wikipedia.org/wiki/Strain_gauge).

There are hundreds of sensing applications. Engineers can use sensors for test and measurement, quality control, force feedback, automation, robotics….the list goes on.  

To lend perspective on what Is possible, FUTEK provides ~250 application landing pages. From an SEO perspective, these are accessible via Google, Safari, even Bing. On FUTEK’s website however, navigating through ~250 applications is not possible through internal search (planned for future development). Let’s design a search tool to change that.

---

## System Design
- **Customer input:** a short description of their application (ie: Laparoscopic Gripper, Robotics, Space Rated Load Cells, etc…)  
- **Application page data:** the 250+ application titles, notes, and URLs stored in JSON  
- **Relevance Algorithm:** based on the provided application description, we design an algorithm to output the top K most relevant URLs to our input query  
- **An API:** to allow communication between an end user and our backend (making it easy for a web dev team to implement the search tool, *winking face emoji* in case you want to implement this @FUTEK_Web_Team).  
