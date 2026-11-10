# gnani_ai_internship-student-copilot-ai
AI-powered multilingual student assistant using voice AI, RAG and intelligent agents
# Student Copilot AI
### A Voice-First, Multilingual AI Companion for Students

<p align="center">

**One student profile. One continuous conversation. Twelve intelligent capabilities.**

</p>

<p align="center">

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi)](https://fastapi.tiangolo.com/)
[![AI](https://img.shields.io/badge/AI-LLM%20Powered-purple)]()
[![Voice](https://img.shields.io/badge/Voice-Gnani.ai-orange)](https://gnani.ai/)
[![Status](https://img.shields.io/badge/Status-Active%20Development-success)]()

</p>

---

## 1. Overview

Student Copilot AI is a voice-first, multilingual academic and career assistant designed to help students manage their learning journey through a unified conversational interface.

Students often switch between multiple platforms to understand difficult concepts, prepare for examinations, debug code, organize study schedules, discover opportunities, prepare resumes, and practice interviews.

Student Copilot brings these workflows together into one intelligent assistant.

The system is designed around a simple idea:

**Students should be able to interact with technology in the language they are comfortable speaking, while receiving technically accurate and structured assistance.**

With multilingual voice interaction, configurable LLM reasoning, document intelligence, personalized student workflows, and specialized assistance modules, Student Copilot aims to make academic and career support more accessible.

### Core Design Principles

- Voice-first interaction rather than relying exclusively on text.
- Support for Telugu, Hindi, English, and code-mixed conversations.
- Context-aware assistance through a continuous student session.
- Specialized workflows instead of one generic chatbot.
- Human control over important application-related actions.
- Privacy-conscious handling of student information and uploaded documents.

---

## 2. Problem Statement

Students face several disconnected challenges throughout their academic journey.

| Problem | Existing Difficulty |
|---|---|
| Learning | Difficult concepts require repeated explanations and personalized teaching. |
| Language barriers | Technical learning resources are frequently English-centric. |
| Study management | Students struggle to organize examinations, assignments, and deadlines. |
| Document understanding | Finding relevant information in lengthy PDFs takes time. |
| Coding | Students often need guidance rather than complete solutions. |
| Career preparation | Resume building, interviews, and skill-gap identification require separate tools. |
| Opportunities | Finding internships, scholarships, and hackathons is fragmented. |
| Personalization | Generic chatbots often lack continuity across different student workflows. |

### Proposed Solution

A unified AI companion that understands student requests, identifies their intent, and routes them to the appropriate capability while maintaining session-level context.

---

## 3. System Architecture

The application follows a modular architecture built around a FastAPI backend, configurable language-model providers, Gnani voice services, and specialized student-assistance workflows.

### High-Level Architecture

```text
                 STUDENT
                    |
                    v
          VOICE / TEXT INTERFACE
                    |
                    v
           FASTAPI APPLICATION
                    |
                    v
          INPUT PROCESSING LAYER
                    |
          +---------+----------+
          |                    |
          v                    v
    LANGUAGE DETECTION     INTENT ROUTER
          |                    |
          +---------+----------+
                    |
                    v
            SESSION CONTEXT
                    |
                    v
          SPECIALIZED MODULES
                    |
      +-------------+--------------+
      |             |              |
      v             v              v
   LEARNING      DOCUMENT        CAREER
   ASSISTANT   INTELLIGENCE     ASSISTANT
      |             |              |
      v             v              v
   CODING        EXAM           OPPORTUNITY
   MENTOR       MANAGER           FINDER
      |             |              |
      +-------------+--------------+
                    |
                    v
             AI REASONING LAYER
                    |
         +----------+-----------+
         |          |           |
         v          v           v
       GROQ       GEMINI     ANTHROPIC
                    |
                    v
             RESPONSE GENERATION
                    |
                    v
            TEXT / VOICE OUTPUT
                    |
                    v
                 STUDENT
```

The architecture represents the logical application flow. Individual modules use different internal processing paths depending on the request.

### Voice Processing Pipeline

```text
Student Speech
      |
      v
Audio Capture
      |
      v
Gnani Prisma STT
      |
      v
Transcribed Text
      |
      v
Language & Intent Detection
      |
      v
AI Processing
      |
      v
Response Generation
      |
      v
Gnani Timbre TTS
      |
      v
Audio Response
```

The application also supports text interaction and browser speech fallback.

---

## 4. Twelve-Module Feature Architecture

The application is organized into twelve specialized capabilities.

### M1 — Voice Intelligence

Provides natural voice interaction through Gnani.ai speech services.

Capabilities:

- Push-to-talk voice interaction.
- Telugu, Hindi, and English language support.
- Telugu-English and Hindi-English code-mixed conversations.
- Speech-to-text using Gnani Prisma.
- Text-to-speech using Gnani Timbre.
- Voice response generation.
- Wake-word and hands-free interaction support.
- Browser Web Speech fallback.

**Integration:**
- STT: `POST /stt/v3`
- TTS: `POST /api/v1/tts/inference`

### M2 — AI Doubt Solver

An adaptive academic doubt-solving assistant.

Capabilities:

- Five progressive explanation levels.
- Simple-to-advanced explanations.
- Real-world analogies.
- Technical examples.
- Telugu-English conversational explanations.
- Image-based doubt solving.
- Context-aware follow-up questions.

### M3 — Learning Assistant

Focuses on improving conceptual understanding rather than simply generating answers.

Capabilities:

- Adaptive explanation depth.
- Prerequisite identification.
- Concept clarification.
- Interactive concept checks.
- Personalized teaching workflows.
- Learning-oriented responses.

### M4 — Document Intelligence

Allows students to interact with their academic documents.

Capabilities:

- PDF upload and parsing using PyMuPDF.
- Document text extraction.
- BM25-based page retrieval.
- Relevant page-level citations.
- Document-based question answering.
- Automatic notes generation.

Supported note formats:

- Short notes.
- Detailed notes.
- Flashcards.
- Formula sheets.
- Examination-oriented notes.

### M5 — Exam Preparation

Helps students organize and prepare for examinations.

Capabilities:

- Interactive topic-based quizzes.
- Quiz answer evaluation.
- Instant explanations.
- Quiz history.
- Syllabus PDF analysis.
- Interactive syllabus checklists.
- Previous-year question paper analysis.
- Important topic extraction.

### M6 — Study Manager

A centralized academic task and planning assistant.

Capabilities:

- Assignment management.
- Task creation and completion tracking.
- Examination revision plans.
- Personalized study schedules.
- Daily study summaries.
- Today's Focus dashboard.
- Missed-session rescheduling.
- Study activity tracking.

### M7 — Coding Mentor

An AI-powered coding assistant designed to guide students through programming problems.

Capabilities:

- Code explanation.
- Error analysis.
- Debugging guidance.
- Programming concept explanations.
- DSA hint-first learning.
- Progressive hints without immediately revealing complete solutions.

Supported programming languages include:

- Python
- Java
- C
- C++
- JavaScript
- SQL
- TypeScript

### M8 — Project Assistant

Helps students identify projects aligned with their interests and existing skills.

Capabilities:

- Profile-based project recommendations.
- Skill-aware project suggestions.
- Hackathon-related assistance.
- Project development guidance.

### M9 — Opportunity Finder

A centralized opportunity discovery and eligibility-assistance module.

Supported categories:

- Internships.
- Scholarships.
- Hackathons.
- Jobs.
- Entrance examinations.
- Admissions.
- Government schemes.
- Certification courses.

Capabilities:

- Opportunity filtering.
- Eligibility checking.
- Required-field identification.
- Missing information detection.
- Deadline information.

**Important:** Current opportunity records are synthetic demonstration data, not verified live listings.

### M10 — Application Agent

An application-assistance workflow designed around transparency and explicit student consent.

Workflow:

1. Select an opportunity.
2. Check eligibility.
3. Identify required application information.
4. Collect missing fields.
5. Generate an application review summary.
6. Request explicit user confirmation.
7. Process the demonstration confirmation workflow.

The application uses a cryptographically generated, single-use confirmation token with a five-minute validity period.

Current application records are synthetic. The workflow does not submit applications to external organizations.

### M11 — Career Assistant

Provides career preparation and professional development assistance.

Capabilities:

- Target-role skill-gap analysis.
- Resume improvement suggestions.
- Resume creation assistance.
- Mock interview preparation.
- Interview answer evaluation.
- HR interview practice.
- Technical interview practice.
- Machine learning interview practice.
- SQL interview practice.
- DSA interview practice.
- GitHub portfolio improvement.
- LinkedIn profile improvement.
- Personal website and blog suggestions.

### M12 — Student Intelligence

Provides personalized learning insights using available session information.

Capabilities:

- Learning activity tracking.
- Study streak tracking.
- Weak-topic identification.
- Quiz performance insights.
- Personalized learning roadmaps.
- Technical terminology explanations.
- Context-aware intent detection.

---

## 5. Technology Stack

| Layer | Technology |
|---|---|
| Backend | Python |
| API Framework | FastAPI |
| ASGI Server | Uvicorn |
| Voice STT | Gnani Prisma |
| Voice TTS | Gnani Timbre |
| LLM Provider | Groq / Gemini / Anthropic |
| Default LLM Configuration | Llama 3.3 70B Versatile |
| PDF Processing | PyMuPDF |
| Retrieval | BM25-based retrieval |
| Data Validation | Pydantic |
| HTTP Communication | HTTPX |
| Environment Management | python-dotenv |
| Testing Framework | Pytest |
| Frontend | HTML, CSS, JavaScript |

### Configurable AI Reasoning

The backend supports configurable reasoning providers:

- Groq
- Google Gemini
- Anthropic
- Mock mode for offline demonstration

The provider is selected through environment configuration rather than hardcoding credentials into the application.

---

## 6. Gnani.ai Integration

Voice interaction is a central part of Student Copilot.

The application integrates Gnani.ai voice capabilities through its configured API services.

### Speech-to-Text — Gnani Prisma

Used to convert student speech into text before processing.

Current integration configuration:

- Service: Gnani Prisma.
- Model configuration: v3.0.
- Supported language configuration: Telugu (`te-IN`) and English (`en-IN`).
- Endpoint: `POST /stt/v3`.

### Text-to-Speech — Gnani Timbre

Used to convert generated responses into spoken audio.

Current integration configuration:

- Service: Gnani Timbre.
- Primary voice configuration: Vasudha v3.0.
- Fallback voice configuration: Varuni v2.5.
- Endpoint: `POST /api/v1/tts/inference`.

### Voice Processing Considerations

- Asynchronous HTTP communication.
- Controlled speech-generation concurrency.
- Audio buffering in memory.
- Browser speech fallback.
- Separate speech recognition and speech synthesis workflows.

The reasoning layer is independently configurable. Gnani voice integration should not be confused with the LLM reasoning provider.

---

## 7. Project Structure

```text
student-copilot-ai/
│
├── app.py
│
├── static/
│   ├── index.html
│   ├── styles.css
│   ├── app.js
│   └── favicon.svg
│
├── tests/
│   ├── test_app.py
│   ├── test_new_features.py
│   └── test_all_12_modules.py
│
├── requirements.txt
├── requirements-dev.txt
├── pytest.ini
│
├── .env.example
├── .gitignore
│
└── README.md
```

### Important Files

| File | Responsibility |
|---|---|
| `app.py` | FastAPI backend, application logic, API routes, AI integrations and session management. |
| `static/index.html` | Main application interface. |
| `static/styles.css` | Frontend styling. |
| `static/app.js` | Frontend interactions and voice handling. |
| `tests/` | Automated application tests. |
| `requirements.txt` | Runtime dependencies. |
| `requirements-dev.txt` | Development and testing dependencies. |
| `.env.example` | Environment variable template. |
| `pytest.ini` | Pytest configuration. |

---

## 8. Installation and Setup

### Prerequisites

- Python 3.10 or later.
- Git.
- A Gnani.ai API key for live voice functionality.
- A supported LLM API key for live reasoning functionality.

### Step 1 — Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/student-copilot-ai.git

cd student-copilot-ai
```

### Step 2 — Create a Virtual Environment

**Windows:**

```powershell
python -m venv .venv

.\.venv\Scripts\Activate.ps1
```

**Linux / macOS:**

```bash
python3 -m venv .venv

source .venv/bin/activate
```

### Step 3 — Install Dependencies

For development:

```bash
pip install -r requirements-dev.txt
```

For runtime only:

```bash
pip install -r requirements.txt
```

### Step 4 — Configure Environment Variables

Create your local environment file.

**Windows:**

```powershell
copy .env.example .env
```

**Linux / macOS:**

```bash
cp .env.example .env
```

### Step 5 — Configure Mock Mode

For an offline demonstration without external API credentials:

```env
MOCK_MODE=true
LLM_PROVIDER=mock
```

### Step 6 — Configure Live AI Mode

To enable Gnani voice services and Groq reasoning:

```env
MOCK_MODE=false

GNANI_API_KEY=your_gnani_api_key
GNANI_BASE_URL=https://api.vachana.ai

LLM_PROVIDER=groq
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile

SESSION_TTL_SECONDS=3600
```

For Gemini reasoning, configure:

```env
MOCK_MODE=false

LLM_PROVIDER=gemini
GEMINI_API_KEY=your_gemini_api_key
LLM_MODEL=your_supported_gemini_model
```

For Anthropic reasoning, configure:

```env
MOCK_MODE=false

LLM_PROVIDER=anthropic
ANTHROPIC_API_KEY=your_anthropic_api_key
LLM_MODEL=your_supported_anthropic_model
```

Use model identifiers supported by the respective provider accounts.

### Step 7 — Start the Application

```bash
python -m uvicorn app:app --reload --port 8000
```

Open the application:

```text
http://127.0.0.1:8000
```

FastAPI interactive API documentation:

```text
http://127.0.0.1:8000/docs
```

Alternative API documentation:

```text
http://127.0.0.1:8000/redoc
```

---

## 9. API Reference

The application exposes REST endpoints grouped by functionality.

### Core and Session Management

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Main application interface |
| GET | `/api/health` | Basic health check |
| GET | `/api/health/detailed` | Detailed module status |
| POST | `/api/session` | Create student session |
| DELETE | `/api/session/{session_id}` | Delete session |
| GET | `/api/profile` | Retrieve student profile |
| PUT | `/api/profile` | Update student profile |
| GET | `/api/progress` | Retrieve student progress |

### Voice and Conversation

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/turn` | Process conversational request |
| POST | `/api/turn/audio` | Process an audio conversation |
| POST | `/api/transcribe` | Speech-to-text |
| POST | `/api/tts` | Text-to-speech |
| POST | `/api/conversation/clear` | Clear conversation context |
| POST | `/api/doubts/image` | Process image-based doubts |

### Documents and Examination

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/documents` | Upload PDF |
| DELETE | `/api/documents` | Remove uploaded documents |
| POST | `/api/documents/notes` | Generate document-based notes |
| POST | `/api/exam/syllabus` | Analyze syllabus |
| GET | `/api/exam/syllabus` | Retrieve syllabus |
| PATCH | `/api/exam/syllabus/topic` | Update topic completion |
| POST | `/api/exam/papers` | Analyze question papers |
| POST | `/api/quiz/start` | Start a quiz |
| POST | `/api/quiz/answer` | Submit quiz answer |
| GET | `/api/quiz/history` | Retrieve quiz history |

### Study Management

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/study/plan` | Generate study plan |
| GET | `/api/study/plan` | Retrieve study plan |
| POST | `/api/study/reschedule` | Reschedule study plan |
| GET | `/api/tasks` | Retrieve tasks |
| POST | `/api/tasks` | Create task |
| PATCH | `/api/tasks/{task_id}` | Update task |
| DELETE | `/api/tasks/{task_id}` | Delete task |
| GET | `/api/today` | Retrieve daily focus |
| POST | `/api/track/activity` | Track learning activity |

### Coding and Project Assistance

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/code/explain` | Explain code and errors |
| POST | `/api/code/dsa-hint` | Generate progressive DSA hints |
| POST | `/api/projects/ideas` | Generate project ideas |

### Opportunities and Applications

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/opportunities` | List opportunities |
| GET | `/api/opportunities/{opportunity_id}` | Retrieve opportunity details |
| POST | `/api/applications/start` | Start application workflow |
| POST | `/api/applications/answer` | Submit application information |
| POST | `/api/applications/confirm` | Confirm demonstration application |

### Career Assistance

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/career/skill-gap` | Analyze skill gaps |
| POST | `/api/career/resume-tips` | Generate resume suggestions |
| POST | `/api/career/interview/start` | Start mock interview |
| POST | `/api/career/interview/answer` | Evaluate interview answer |
| GET | `/api/career/interview/status` | Retrieve interview status |
| POST | `/api/career/portfolio` | Generate portfolio suggestions |

### Student Intelligence

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/analytics` | Retrieve learning analytics |
| POST | `/api/learn/path` | Generate learning roadmap |
| GET | `/api/learn/term` | Explain technical terminology |

### Configuration

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/config/llm-key` | Update Groq key at runtime |

All request schemas and response formats can be explored through the interactive Swagger documentation at `/docs`.

**Deployment note:** The runtime LLM-key configuration endpoint must be protected or disabled before public deployment. Never expose credential-management functionality without proper authentication and authorization.

---

## 10. Security, Privacy and Responsible AI

Student Copilot is designed with explicit user control and privacy-conscious processing.

### Synthetic Demonstration Data

- Opportunity records are fictional.
- Application workflows are demonstrations.
- No real external application submission is performed.
- Demo records must not be interpreted as verified opportunities.

### Session Management

- Student information is maintained in session-level application state.
- Sessions have a configurable expiration period.
- Expired sessions are cleaned up.
- Session data is currently in memory and is not durable across application restarts.

### Voice and Document Handling

- Audio processing uses in-memory buffering in the current implementation.
- Uploaded documents are associated with the active session.
- Users can remove uploaded documents through the application workflow.

### Application Consent

- Application information is collected transparently.
- A review and confirmation step is required.
- One-time confirmation tokens are used in the demonstration workflow.

### Security Controls

- Environment-based API credential configuration.
- Request validation through Pydantic.
- Request rate limiting.
- Constant-time comparison for demo access tokens.
- Security response headers.
- Content Security Policy.
- Restricted microphone permissions.

**Security scope:** These controls are application-level safeguards, not a certification of compliance with the Digital Personal Data Protection Act or a complete production security audit. Production deployment requires additional security, authentication, storage, retention, and privacy reviews.

---

## 11. Testing

The project uses Pytest for automated testing.

Run the test suite:

```bash
python -m pytest tests/ -v
```

Run tests with a shorter output:

```bash
python -m pytest tests/ -q
```

Run a specific test file:

```bash
python -m pytest tests/test_app.py -v
```

Testing should cover:

- API request and response validation.
- Session creation and expiration.
- Conversation handling.
- Voice integration behavior.
- Document processing.
- Study management.
- Quiz functionality.
- Coding assistance.
- Opportunity and application workflows.
- Career assistance.
- Security controls.

Actual test results should be reported from the latest test execution.

---

## 12. Current Implementation Scope and Limitations

The current version is a functional prototype with multiple integrated student-assistance workflows.

Important implementation boundaries:

| Area | Current Scope |
|---|---|
| Session storage | In-memory |
| Opportunity data | Synthetic demonstration records |
| Application workflow | Demonstration only |
| LLM reasoning | Configurable external providers and mock mode |
| Voice processing | Gnani API integration with browser fallback |
| Document retrieval | BM25-based retrieval |
| Persistence | No production database configured |
| Deployment | Local development setup |

These boundaries are intentional documentation of the current implementation, not claims of production readiness.

---

## 13. Future Improvements

The following improvements are potential development directions:

- Persistent storage using PostgreSQL.
- Distributed session management using Redis.
- Authentication and role-based access control.
- Production-grade document storage and lifecycle management.
- Hybrid retrieval combining BM25 and vector search.
- Cross-encoder reranking for document retrieval.
- LangGraph-based multi-agent orchestration.
- Tool-calling workflows with controlled permissions.
- Improved conversation memory.
- Evaluation datasets for answer quality and retrieval accuracy.
- Voice latency and transcription-quality benchmarks.
- Deployment with monitoring and observability.
- Verified external opportunity integrations.
- Production-grade consent and application integrations.

Future improvements will be added incrementally and documented as they are implemented and validated.

---

## 14. Why Student Copilot?

Student Copilot is built around a unified student experience rather than treating academic support, career preparation, voice interaction, and opportunity assistance as unrelated applications.

The project explores how multiple AI capabilities can be organized into a single system with:

- Natural multilingual interaction.
- Context-aware workflows.
- Specialized task routing.
- Configurable LLM reasoning.
- Document-based assistance.
- Human-controlled actions.

The objective is not simply to build another chatbot, but to explore practical AI system engineering through an integrated application.

---

## 15. Author

**Kunchakuri Sathwik**

B.Tech — Computer Science and Engineering (AI & ML)

Interests:
- Artificial Intelligence
- Machine Learning and Deep Learning
- Large Language Models
- Generative AI
- Retrieval-Augmented Generation
- AI Agents and Orchestration
- Voice AI

---

## 16. Acknowledgements

Special acknowledgement to **Gnani.ai** for its voice AI technologies and the opportunity to explore practical applications of multilingual conversational AI through the Great Indian AI Internship Challenge.

---

<p align="center">

**Student Copilot AI**

*Making intelligent student assistance more accessible, conversational, and personalized.*

</p>
