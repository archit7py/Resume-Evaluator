AI Resume Parser & Job Matcher

A Python tool that uses an LLM (via Groq) to parse job descriptions and resumes into structured data, then scores how well each resume matches the job — automatically, in batch, straight from a folder of PDF/DOCX files.

What it does
Parses a job description into structured fields: role, required skills, preferred skills, minimum experience, education requirements, and responsibilities.
Extracts text from resumes — supports .pdf, .docx, and .txt files.
Parses each resume into structured fields: name, contact info, total experience, skills, work history, education, projects, and certifications.
Scores each resume against the job description based on:
Required skill overlap (60% weight)
Preferred skill overlap (20% weight)
Years of experience vs. minimum required (20% weight)
Ranks all resumes from best to worst match, with a breakdown of matched/missing skills for each.
How it works

Everything runs through the Groq API using llama-3.3-70b-versatile, with structured JSON output enforced via Pydantic schemas — so the LLM's output is always validated against a strict, predictable format rather than free-form text.

Requirements
Python 3.11+
A free Groq API key
uv (recommended) for dependency management
Setup
Clone the repo:
bash
   git clone https://github.com/archit7py/resume-parser-ai.git
   cd resume-parser-ai
Install dependencies:
bash
   uv add groq pydantic python-dotenv pypdf python-docx
Create a .env file in the project root with your Groq API key:
   GROQ_API_KEY=your_api_key_here
Create a resumes/ folder in the project root and drop in the resume files you want to evaluate (.pdf, .docx, or .txt).
Usage

Run against all resumes in the default resumes/ folder:

bash
uv run resume_parser.py

Point it at a different folder:

bash
uv run resume_parser.py path/to/other_folder

Or run it against specific files:

bash
uv run resume_parser.py resume1.pdf resume2.docx
Example output
=== Job Description Parsed ===
AI / ML Engineer
5.0
['Computer Science', 'Artificial Intelligence', 'Machine Learning']

Found 3 resume(s) to process.

=== Processing: resumes/varad_resume.pdf ===
Name: Varad Bhogayata
Experience: 2.0 years
Skills: ['Python', 'TensorFlow', 'PyTorch', 'Docker', 'AWS', ...]
Score: 37.14%

=== Ranking (best match first) ===
1. Varad Bhogayata - 37.14%
2. Soumyajit Behera - 26.86%
3. Archit Prasad - 22.86%
Project structure
project_1/
├── resume_parser.py     # main script
├── pyproject.toml       # uv project config & dependencies
├── .env                 # your Groq API key (not committed)
├── .gitignore
└── resumes/             # drop resume files here (not committed)
Customizing
Job description: edit the job_description string near the top of resume_parser.py.
Matching weights: adjust the 0.6 / 0.2 / 0.2 weighting inside match_resume_to_job() to prioritize skills vs. experience differently.
Model: swap the model variable to any other Groq-hosted model if needed.
Known limitations
Scanned/image-based PDFs (no text layer) can't be read without OCR — the script will raise a clear error if this happens.
Skill matching is currently exact-string based (case-insensitive), so close-but-not-identical phrasing (e.g. "ML" vs. "Machine Learning") may not match perfectly.
Experience extraction depends on how clearly a resume states total years of experience.
Roadmap ideas
Fuzzy/semantic skill matching instead of exact string overlap
Export ranked results to CSV/Excel
Simple web UI for drag-and-drop resume upload
