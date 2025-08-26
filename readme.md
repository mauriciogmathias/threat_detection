# Threat Detection (STRIDE Modeler)

A simple **Threat Modeling Tool** that uses **Azure OpenAI** and the **STRIDE methodology** to analyze application architectures.  
It provides a **FastAPI back end** that generates a structured threat model from an architecture diagram + system description, and a **front-end** page that lets you upload the diagram and visualize threats as a graph.

---

## 📦 Project Structure

    .
    ├── back-end/
    │   └── main.py        # FastAPI server: Azure OpenAI call + STRIDE prompt
    ├── front-end/
    │   └── index.html     # Bootstrap form + Cytoscape visualization
    ├── .gitignore
    └── README.md

---

## ⚙️ Requirements

Python packages (minimum):
- `openai`
- `fastapi`
- `uvicorn`
---

## 🧠 How it Works (STRIDE)

The back end builds a detailed prompt (in English) instructing the model to analyze your inputs and produce:
- A JSON array of threats categorized by **STRIDE**:
  - **S**poofing (identity forgery)
  - **T**ampering (data/request modification)
  - **R**epudiation (denying actions)
  - **I**nformation Disclosure (sensitive data leaks)
  - **D**enial of Service (service overload/disruption)
  - **E**levation of Privilege (unauthorized admin-level access)
- An array of **improvement suggestions** (what extra info would make the threat model more precise).

The **front end**:
- Lets you upload an **architecture image** and fill in system details.
- Shows the **raw JSON text** returned.
- Renders a **threat graph** using Cytoscape and includes a button to print the graph.