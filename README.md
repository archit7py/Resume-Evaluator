# 📄 Resume Evaluator AI

An AI-powered Resume Evaluator that extracts structured information from resumes and compares it against a job description to determine how well a candidate matches a role.

Built using **Python**, **Pydantic**, **Groq LLM**, and **PDF/DOCX parsing**.

---

## 🚀 Features

- 📄 Extract text from PDF and DOCX resumes
- 🤖 AI-powered resume information extraction using Groq LLM
- ✅ Structured output validation using Pydantic
- 💼 Parse job descriptions into structured data
- 🎯 Compare resume with job requirements
- 📊 Calculate candidate-job match score
- 📝 Generate detailed evaluation report

---

## 🛠️ Tech Stack

- Python 3.11+
- Groq API
- Pydantic
- python-dotenv
- PyPDF
- python-docx
- UV (Package Manager)

---

## 📂 Project Structure

```
project_1/
│
├── main.py
├── models.py
├── prompts.py
├── parser.py
├── evaluator.py
├── llm.py
├── pyproject.toml
├── uv.lock
├── README.md
├── .env.example
│
├── resumes/
│   └── sample_resume.pdf
│
└── output/
```

---

## ⚙️ Installation

Clone the repository

```bash
git clone https://github.com/yourusername/Resume-Evaluator.git

cd Resume-Evaluator
```

Install dependencies

```bash
uv sync
```

or

```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Create a `.env` file.

```env
GROQ_API_KEY=your_api_key_here
```

---

## ▶️ Run

```bash
python main.py
```

---

## 📈 Workflow

```
Resume (PDF/DOCX)
        │
        ▼
Text Extraction
        │
        ▼
Groq LLM
        │
        ▼
Structured Resume (Pydantic)
        │
        ▼
Job Description Parser
        │
        ▼
Matching Engine
        │
        ▼
Candidate Score + Report
```

---

## 🧠 How It Works

1. Upload a resume.
2. Extract text from the document.
3. Convert unstructured text into structured JSON using Groq.
4. Validate the extracted data with Pydantic.
5. Parse the job description.
6. Compare:
   - Skills
   - Experience
   - Education
   - Projects
7. Generate an overall compatibility score.

---

## 📊 Example Output

```text
Candidate Name : John Doe

Skills Match      : 90%
Experience Match : 80%
Education Match  : 100%
Projects Match   : 75%

Overall Score    : 86%
```

---

## 🔮 Future Improvements

- Streamlit Web Interface
- Multi-resume evaluation
- ATS Compatibility Score
- Skill Gap Analysis
- Resume Improvement Suggestions
- Interview Question Generator
- Export results to PDF
- Batch resume processing

---

## 🤝 Contributing

Contributions, suggestions, and improvements are welcome.

Feel free to fork the repository and submit a pull request.

---

## 📜 License

This project is licensed under the MIT License.

---

## 👨‍💻 Author

**Archit Prashad**

- GitHub: https://github.com/archit7py
- LinkedIn: *(Add your LinkedIn profile here)*

---

⭐ If you found this project useful, consider giving it a star!
