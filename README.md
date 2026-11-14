# French Tutor AI — Grammar Checker with LLMs and RAG

An academic AI project designed to help French-language learners **identify**, **correct**, and **understand** grammatical mistakes in their writing.

The application follows a three-stage workflow: **Grammar Error Detection (GED)**, **Grammar Error Correction (GEC)**, and **Grammar Error Feedback (GEF)**. It uses an LLM-based approach and retrieval-augmented generation (RAG) to support explanations with relevant grammar knowledge.

> **Project type:** University team project, Introduction to AI, University of Science and Technology of Hanoi (USTH), academic year 2025–2026.  
> **My contribution (Pham Duc Minh):** Grammar Error Detection (GED) and related setup.

## Main features

- **Detect errors:** Identify the location and category of errors in a French sentence.
- **Suggest corrections:** Produce a corrected sentence.
- **Explain mistakes:** Return grammar-oriented feedback to help learners understand the correction.
- **Web demonstration:** Provide a browser-based interface for trying the workflow.

## How the system works

```text
French sentence (user input)
          |
          v
 GED: detect grammar errors and categories
          |
          v
 GEC: generate a corrected sentence
          |
          v
 GEF: retrieve relevant grammar knowledge (RAG)
      and generate an explanation
          |
          v
 Error list + corrected sentence + feedback
```

The team presentation describes **few-shot prompting** for error detection, **instruction-based generation** for correction, and a RAG-assisted explanation component.

## Technologies

- **Language:** Python
- **LLM:** OpenAI GPT-4o-mini (as described in the project presentation)
- **LLM orchestration:** LangChain
- **Embeddings:** `paraphrase-multilingual-MiniLM-L12-v2` (Sentence Transformers)
- **Vector search:** FAISS
- **Web interface:** Gradio

These technologies reflect the project presentation. The exact versions and runtime configuration should be verified against the source code before publishing a reproducible release.

## Repository structure

```text
french-AI-tutor/
├── main.py          # Application entry point / web demo
├── ged.py           # Grammar Error Detection
├── gec.py           # Grammar Error Correction
├── gef.py           # Grammar Error Feedback
├── knowledge.txt    # Grammar knowledge resource
└── README.txt       # Original Vietnamese run instructions
```

## Run locally

**Prerequisites:** Python 3 and access to any external API required by the code.

1. Clone the repository:

   ```bash
   git clone https://github.com/Minhpd-1704/french-AI-tutor.git
   cd french-AI-tutor
   ```

2. Create and activate a virtual environment (optional but recommended):

   **Windows PowerShell:**
   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

3. Install the packages listed in the original run instructions:

   ```bash
   pip install openai gradio langchain langchain-community langchain-huggingface sentence-transformers faiss-cpu
   ```

4. **Configure the API credentials safely.** If the code uses OpenAI, keep your API key outside the repository (for example, in an environment variable named `OPENAI_API_KEY`). Check the actual Python source for the name and method it expects. Do **not** commit real keys.

5. Launch the application:

   ```bash
   python main.py
   ```

6. Open the local URL displayed in the terminal. According to the original instructions, the default address is:

   `http://127.0.0.1:7860`

> **Setup note:** The commands above reproduce the existing `README.txt` instructions, but have not been independently tested against the live repository. A pinned `requirements.txt` would improve reproducibility.

## Example use case

**Input:** `Je suis aller au marché.`  
**Expected type of feedback:** Highlight the incorrect past participle, suggest `Je suis allé au marché.`, and explain the use of *être* and the past participle in the *passé composé*.

*This is an illustrative example, not a recorded model evaluation result.*

## Evaluation and limitations

The project demonstrates a modular French grammar tutoring workflow. The available presentation does not report a validated benchmark accuracy for each module, so no performance claim is made here.

Potential limitations include inaccurate corrections, incomplete grammar explanations, sensitivity to prompt wording, and dependence on external model availability. Learners should review AI-generated feedback critically.

## Contributions and attribution

This was a **team project**. My documented responsibility was the **Grammar Error Detection (GED)** component and related setup. The correction module, feedback/RAG module, data preparation, interface, and integration were developed collaboratively or by other team members.

If this repository was copied from a university or team repository, retain attribution to the original project and confirm permission to publish shared code and assets.

## Suggested improvements

- Add `requirements.txt` with tested versions and a `.gitignore` that excludes `.env`, `.venv/`, caches, and credentials.
- Add an example configuration file (without real secrets).
- Add screenshots of the Gradio interface and one complete example output.
- Add reproducible test cases and module-level evaluation metrics.
- Link to the original team repository if applicable.
