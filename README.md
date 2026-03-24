# SDE-3 MERN Interview Kit Generator (CrewAI)

This project uses a multi-agent `CrewAI` workflow to generate a professional **SDE-3 MERN Stack Tech Lead Interview Kit**.

The script orchestrates multiple specialist agents (process design, MERN technical depth, system design, and evaluator) and produces:
- A final Markdown interview kit
- A DOCX version for sharing/printing
- A detailed execution log

## What It Generates

For each run, the script creates timestamped files in the project root:
- `SDE3_MERN_Interview_Kit_<timestamp>.md`
- `SDE3_MERN_Interview_Kit_<timestamp>.docx`
- `sde3_mern_interview_logs_<timestamp>.log`

The generated kit includes:
- 4-round interview process
- Senior-level MERN technical questions
- System design questions with trade-off guidance
- Model answers for key questions
- Scoring rubric (1-10 scale)
- Suggested diagram ideas

## Tech Stack

- Python 3.10+
- [CrewAI](https://github.com/crewAIInc/crewAI)
- Google Gemini via `langchain-google-genai`
- `python-dotenv`
- `tenacity`
- `python-docx`

## Project File

Main script:
- `agent_ochestrating_crewai_demo.py`

## Setup

1. Create and activate a virtual environment (recommended):

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

2. Install dependencies:

```powershell
pip install crewai langchain-google-genai python-dotenv tenacity google-api-core python-docx
```

3. Create a `.env` file in the project root:

```env
GEMINI_API_KEY=your_gemini_api_key_here
```

> `OPENAI_API_KEY` is not required by the current script.

## Run

```powershell
python agent_ochestrating_crewai_demo.py
```

After completion, check the generated `.md`, `.docx`, and `.log` files in the same folder.

## Notes

- The script uses `gemini-2.5-flash` with retry/backoff handling for rate limits.
- Crew execution is sequential with memory enabled.
- Output is timestamped to preserve history across multiple runs.

## Security

- Do **not** commit `.env` to version control.
- If API keys are ever exposed, rotate them immediately.

## Suggested Next Improvements

- Add a `requirements.txt` file for reproducible installs.
- Add CLI args (role level, number of questions, output format).
- Split agent/task definitions into modules for maintainability.
