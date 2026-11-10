# Student Copilot AI
### A Voice-First, Multilingual AI Companion for Students

<p align="center">

**One Student Profile. One Continuous Conversation. Twelve Intelligent Capabilities.**

</p>

<p align="center">

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688?logo=fastapi)](https://fastapi.tiangolo.com/)
[![AI](https://img.shields.io/badge/AI-LLM%20Powered-purple)](https://en.wikipedia.org/wiki/Large_language_model)
[![Voice AI](https://img.shields.io/badge/Voice-Gnani.ai-orange)](https://gnani.ai/)
[![Status](https://img.shields.io/badge/Status-Active%20Development-success)]()

</p>

---

## 1. Overview

Student Copilot AI is a voice-first, multilingual academic and career companion designed to simplify the complete student journey through a unified conversational interface.

Students frequently switch between different applications and platforms to understand difficult concepts, prepare for examinations, organize study schedules, debug programming errors, analyze academic documents, discover opportunities, prepare resumes, and practice interviews.

Student Copilot brings these disconnected workflows together into one intelligent AI companion.

The platform is designed especially for Indian engineering students who may prefer communicating in Telugu or Hindi while learning and coding in English.

Instead of navigating multiple applications, students can interact with a single assistant using voice or text and receive context-aware assistance across different academic and professional workflows.

### Core Vision

**Make intelligent academic and career assistance accessible through natural, multilingual, personalized conversations.**

### Core Design Principles

- Voice-first and conversational interaction.
- Telugu, Hindi, English, and code-mixed communication.
- Continuous session-level student context.
- Specialized AI capabilities for different student needs.
- Adaptive learning instead of generic answer generation.
- Human-controlled actions for sensitive workflows.
- Privacy-conscious document and audio handling.

---

## 2. Problem Statement

Students face several disconnected challenges throughout their academic and professional development.

| Problem Area | Student Challenge |
|---|---|
| Learning | Understanding difficult concepts requires repeated explanations. |
| Language barriers | Many technical learning resources are English-centric. |
| Document understanding | Extracting relevant information from lengthy PDFs takes time. |
| Examination preparation | Organizing syllabi, previous papers, and revision schedules is difficult. |
| Coding | Students need debugging guidance and problem-solving hints. |
| Study management | Assignments, deadlines, and revision plans are difficult to coordinate. |
| Opportunities | Discovering relevant internships, scholarships, and hackathons is fragmented. |
| Career preparation | Resume improvement, skill-gap analysis, and interview preparation require separate tools. |
| Personalization | Generic AI assistants often lack continuity across different student workflows. |

### Proposed Solution

Student Copilot provides a unified AI interface that understands student requests, identifies their intent, and routes them to specialized capabilities while maintaining session-level context.

---

## 3. System Architecture

The application follows a modular architecture built around a FastAPI backend, configurable LLM providers, Gnani.ai voice services, and specialized student-assistance workflows.

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
       LANGUAGE HANDLING       INTENT ROUTING
              |                    |
              +---------+----------+
                        |
                        v
                 SESSION CONTEXT
                        |
                        v
              SPECIALIZED MODULES
                        |
       +----------------+----------------+
       |                |                |
       v                v                v
   LEARNING         DOCUMENT           CAREER
   ASSISTANT      INTELLIGENCE        ASSISTANT
       |                |                |
       v                v                v
    CODING             EXAM          OPPORTUNITY
    MENTOR            MANAGER           FINDER
       |                |                |
       +----------------+----------------+
                        |
                        v
                AI REASONING LAYER
                        |
             +----------+----------+
             |          |          |
             v          v          v
           GROQ       GEMINI    ANTHROPIC
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

The diagram represents the logical application architecture. Individual modules follow their respective processing workflows.

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
Speech-to-Text
      |
      v
Language & Intent Processing
      |
      v
Student Copilot Processing
      |
      v
AI Response Generation
      |
      v
Gnani Timbre TTS
      |
      v
Audio Response
      |
      v
Student
```

The platform also supports text-based interaction and browser speech fallback.

---

## 4. Twelve-Module Feature Architecture

Student Copilot is organized into twelve specialized capabilities.

| Module | System Component | Primary Responsibility |
|---|---|---|
| M1 | Voice Intelligence | Multilingual speech interaction |
| M2 | AI Doubt Solver | Adaptive academic explanations |
| M3 | Learning Assistant | Personalized conceptual learning |
| M4 | Document Intelligence | PDF understanding and notes generation |
| M5 | Exam Preparation | Syllabus analysis and quizzes |
| M6 | Study Manager | Academic planning and task management |
| M7 | Coding Mentor | Programming and DSA guidance |
| M8 | Project Assistant | Project recommendations |
| M9 | Opportunity Finder | Opportunity discovery and eligibility |
| M10 | Application Agent | Consent-controlled application workflow |
| M11 | Career Assistant | Resume and interview preparation |
| M12 | Student Intelligence | Learning insights and roadmaps |

### M1 — Voice Intelligence

Provides natural voice interaction through Gnani.ai speech services.

**Capabilities:**

- Push-to-talk voice interaction.
- Telugu, Hindi, and English language support.
- Code-mixed conversational interaction.
- Speech-to-text using Gnani Prisma.
- Text-to-speech using Gnani Timbre.
- Voice response generation.
- Wake-word detection support.
- Browser Web Speech fallback.

**Gnani integration:**
- STT: `POST /stt/v3`
- TTS: `POST /api/v1/tts/inference`

### M2 — AI Doubt Solver

An adaptive academic doubt-solving assistant.

**Capabilities:**

- Five progressive explanation levels, from simple explanations to implementation-oriented guidance.
- Misconception identification.
- Real-world analogies.
- Technical examples.
- Telugu-English conversational explanations.
- Image-based doubt solving.
- Context-aware follow-up questions.

### M3 — Learning Assistant

Focuses on improving conceptual understanding rather than simply generating answers.

**Capabilities:**

- Prerequisite identification.
- Adaptive explanation depth.
- Concept clarification.
- Interactive concept checks.
- Personalized teaching workflows.
- Multi-mode learning assistance.

### M4 — Document Intelligence

Allows students to interact with their academic documents.

**Capabilities:**

- PDF upload and parsing using PyMuPDF.
- Document text extraction.
- BM25-based retrieval.
- Relevant page-level citations.
- Document-based question answering.
- Automatic notes generation.

**Supported note formats:**

- Short notes.
- Detailed notes.
- Flashcards.
- Formula sheets.
- Examination-oriented notes.

### M5 — Exam Preparation

Helps students prepare systematically for examinations.

**Capabilities:**

- Interactive topic-based quizzes.
- Quiz answer evaluation.
- Instant explanations.
- Quiz history.
- Syllabus PDF analysis.
- Interactive syllabus checklists.
- Previous-year question paper analysis.
- Important topic extraction.

### M6 — Study Manager

A centralized academic planning and task-management assistant.

**Capabilities:**

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

**Capabilities:**

- Code explanation.
- Error analysis.
- Debugging guidance.
- Programming concept explanations.
- DSA hint-first learning.
- Progressive hints without immediately revealing complete solutions.

**Supported programming languages:**

- Python
- Java
- C
- C++
- JavaScript
- SQL
- TypeScript

### M8 — Project Assistant

Helps students identify projects aligned with their interests, skills, and career goals.

**Capabilities:**

- Profile-based project recommendations.
- Skill-aware project suggestions.
- Hackathon-related assistance.
- Project development guidance.

### M9 — Opportunity Finder

A centralized opportunity discovery and eligibility-assistance module.

**Supported categories:**

1. Internships
2. Scholarships
3. Hackathons
4. Examinations
5. Jobs
6. Admissions
7. Services
8. Courses

**Capabilities:**

- Opportunity filtering.
- Eligibility checking.
- Required-field identification.
- Missing information detection.
- Opportunity detail retrieval.
- Deadline-related information.

**Data transparency:** The current opportunity records are synthetic demonstration data, not verified live listings.

### M10 — Application Agent

An application-assistance workflow designed around transparency and explicit student consent.

**Workflow:**

1. Select an opportunity.
2. Check eligibility.
3. Identify required application information.
4. Collect missing fields.
5. Generate an application review summary.
6. Request explicit user confirmation.
7. Process the demonstration confirmation workflow.

**Safety mechanism:**

- Cryptographically generated one-time confirmation token.
- Five-minute token validity.
- Single-use confirmation.
- Explicit user consent before confirmation.

The current implementation uses synthetic application records and does not submit applications to external organizations.

### M11 — Career Assistant

Provides career preparation and professional development assistance.

**Capabilities:**

- Target-role skill-gap analysis.
- Tailored resume improvement suggestions.
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

**Capabilities:**

- Learning activity tracking.
- Study streak tracking.
- Weak-topic identification.
- Quiz performance insights.
- Personalized multi-week learning roadmaps.
- Telugu-English technical terminology explanations.
- Context-aware intent detection.

---

## 5. Technology Stack

| Layer | Technology |
|---|---|
| Programming Language | Python |
| Backend Framework | FastAPI |
| ASGI Server | Uvicorn |
| Voice Speech Recognition | Gnani Prisma |
| Voice Speech Synthesis | Gnani Timbre |
| LLM Providers | Groq, Google Gemini, Anthropic |
| Default LLM Configuration | Llama 3.3 70B Versatile |
| PDF Processing | PyMuPDF |
| Document Retrieval | BM25 |
| Request Validation | Pydantic |
| HTTP Communication | HTTPX |
| Environment Configuration | python-dotenv |
| Frontend | HTML, CSS, JavaScript |
| Testing | Pytest |

### Configurable AI Reasoning

The backend supports configurable LLM reasoning providers:

- Groq
- Google Gemini
- Anthropic
- Mock mode for offline demonstrations

The provider is selected through environment configuration rather than hardcoding API credentials into application logic.

---

## 6. Gnani.ai Integration

Voice interaction is a central component of Student Copilot.

The application integrates Gnani.ai voice capabilities through its configured API services.

### Speech-to-Text — Gnani Prisma

Converts student speech into text before it enters the conversational processing pipeline.

**Configuration:**

| Parameter | Configuration |
|---|---|
| Service | Gnani Prisma |
| Model version | v3.0 |
| Language configuration | `te-IN`, `en-IN` |
| Format | `transcribe` |
| Endpoint | `POST /stt/v3` |

### Text-to-Speech — Gnani Timbre

Converts generated responses into spoken audio.

**Configuration:**

| Parameter | Configuration |
|---|---|
| Service | Gnani Timbre |
| Primary voice | Vasudha v3.0 |
| Fallback voice | Varuni v2.5 |
| Gender configuration | Female |
| Speed configuration | 1.0 |
| Endpoint | `POST /api/v1/tts/inference` |

### Voice Processing Considerations

- Asynchronous HTTP communication.
- Controlled speech-generation concurrency.
- Sequential speech generation using an asynchronous semaphore.
- Audio buffering in memory.
- Browser speech fallback.
- Separate speech recognition and synthesis workflows.

**Important:** Gnani is responsible for the configured speech services. The language-model reasoning layer is independently configured through the supported LLM providers.

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
| `app.py` | FastAPI backend, application logic, API routes, AI integrations, and session management. |
| `static/index.html` | Main application interface. |
| `static/styles.css` | Frontend styling and design system. |
| `static/app.js` | Frontend state, voice recording, and UI interactions. |
| `static/favicon.svg` | Application brand icon. |
| `tests/` | Automated application tests. |
| `requirements.txt` | Runtime dependencies. |
| `requirements-dev.txt` | Development and testing dependencies. |
| `.env.example` | Environment configuration template. |
| `pytest.ini` | Pytest configuration. |

---

## 8. Installation and Setup

### Prerequisites

- Python 3.10 or later.
- Git.
- Gnani.ai API key for live voice functionality.
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

Create your local environment file from the example.

**Windows:**

```powershell
copy .env.example .env
```

**Linux / macOS:**

```bash
cp .env.example .env
```

### Step 5 — Run in Mock Mode

For an offline demonstration without external API credentials:

```env
MOCK_MODE=true
LLM_PROVIDER=mock
```

Mock mode provides demonstration responses without requiring live external AI services.

### Step 6 — Configure Live Gnani Voice and Groq Reasoning

Add the following configuration to `.env`:

```env
MOCK_MODE=false

GNANI_API_KEY=your_gnani_api_key
GNANI_BASE_URL=https://api.vachana.ai

LLM_PROVIDER=groq
GROQ_API_KEY=your_groq_api_key
GROQ_MODEL=llama-3.3-70b-versatile

SESSION_TTL_SECONDS=3600
```

### Alternative: Gemini Reasoning

```env
MOCK_MODE=false

GNANI_API_KEY=your_gnani_api_key
GNANI_BASE_URL=https://api.vachana.ai

LLM_PROVIDER=gemini
LLM_MODEL=gemini-2.0-flash
GEMINI_API_KEY=your_gemini_api_key
```

Use a model identifier supported by your provider account.

### Step 7 — Start the Application

```bash
python -m uvicorn app:app --reload --port 8000
```

### Step 8 — Access the Application

**Application:**

http://127.0.0.1:8000

**Interactive API Documentation:**

http://127.0.0.1:8000/docs

**Alternative API Documentation:**

http://127.0.0.1:8000/redoc

---

## 9. API Reference

The backend exposes REST APIs organized around the twelve modules.

### Core and Session Management

| Method | Endpoint | Description |
|---|---|---|
| GET | `/` | Main application interface |
| GET | `/api/health` | Basic service health |
| GET | `/api/health/detailed` | Detailed status of all modules |
| POST | `/api/session` | Initialize student session |
| DELETE | `/api/session/{id}` | Clear session and associated state |
| GET / PUT | `/api/profile` | Retrieve or update student profile |

### Voice and Conversation

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/turn` | Process conversational request |
| POST | `/api/turn/audio` | End-to-end voice interaction |
| POST | `/api/transcribe` | Speech-to-text |
| POST | `/api/tts` | Text-to-speech |
| POST | `/api/conversation/clear` | Clear conversation context |
| POST | `/api/doubts/image` | Image-based doubt solving |

### Document Intelligence

| Method | Endpoint | Description |
|---|---|---|
| POST / DELETE | `/api/documents` | Upload or remove documents |
| POST | `/api/documents/notes` | Generate document-based notes |

### Examination and Quizzes

| Method | Endpoint | Description |
|---|---|---|
| POST / GET | `/api/exam/syllabus` | Upload or retrieve syllabus |
| PATCH | `/api/exam/syllabus/topic` | Update topic completion |
| POST | `/api/exam/papers` | Analyze previous question papers |
| POST | `/api/quiz/start` | Start a topic-based quiz |
| POST | `/api/quiz/answer` | Submit an answer |
| GET | `/api/quiz/history` | Retrieve quiz history |

### Study Management

| Method | Endpoint | Description |
|---|---|---|
| POST / GET | `/api/study/plan` | Generate or retrieve study plan |
| POST | `/api/study/reschedule` | Reschedule remaining topics |
| GET / POST | `/api/tasks` | Retrieve or create tasks |
| PATCH / DELETE | `/api/tasks/{id}` | Update or remove tasks |
| GET | `/api/today` | Retrieve daily focus |
| POST | `/api/track/activity` | Track study activity |

### Coding and Project Assistance

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/code/explain` | Explain code and errors |
| POST | `/api/code/dsa-hint` | Generate progressive DSA hints |
| POST | `/api/projects/ideas` | Generate personalized project ideas |

### Opportunities and Applications

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/opportunities` | Retrieve available demonstration opportunities |
| GET | `/api/opportunities/{id}` | Retrieve opportunity details and eligibility |
| POST | `/api/applications/start` | Start application workflow |
| POST | `/api/applications/answer` | Provide application information |
| POST | `/api/applications/confirm` | Confirm demonstration application |

### Career Assistance

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/career/skill-gap` | Analyze target-role skill gaps |
| POST | `/api/career/resume-tips` | Generate resume recommendations |
| POST | `/api/career/interview/start` | Start mock interview |
| POST | `/api/career/interview/answer` | Evaluate interview answer |
| POST | `/api/career/portfolio` | Generate portfolio recommendations |

### Student Intelligence

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/analytics` | Retrieve learning analytics |
| POST | `/api/learn/path` | Generate learning roadmap |
| GET | `/api/learn/term` | Explain technical terminology |

For complete request schemas, parameters, and response structures, use the automatically generated Swagger documentation at `/docs`.

---

## 10. Security, Privacy and Responsible AI

Student Copilot is designed with user control and privacy-conscious processing as important considerations.

### Synthetic Demonstration Data

- Opportunity records are synthetic.
- Application workflows are demonstrations.
- No real external application submission is performed.
- Demonstration records must not be interpreted as verified opportunities.

### Session Management

- Student information is maintained in session-level application state.
- Sessions have a configurable expiration period.
- Session data is held in memory.
- Current session state is not durable across application restarts.

### Audio and Document Handling

- Audio is buffered in memory in the current implementation.
- Uploaded documents are associated with the active session.
- Users can remove uploaded documents through the application workflow.

### Application Consent

- Application information is collected transparently.
- A review and confirmation step is required.
- One-time confirmation tokens are used in the demonstration workflow.
- The system does not bypass external authentication or CAPTCHA mechanisms.

### Security Controls

- Environment-based API credential configuration.
- Pydantic request validation.
- Request rate limiting.
- Constant-time comparison for demo access tokens.
- Security response headers.
- Content Security Policy.
- Restricted microphone permissions.

**Security scope:** These are application-level safeguards, not a certification of compliance with the Digital Personal Data Protection Act (DPDP Act) or a complete production security audit. Production deployment requires additional authentication, authorization, encryption, retention, storage, and privacy reviews.

---

## 11. Automated Testing

The project uses Pytest for automated testing.

### Run the Complete Test Suite

```bash
python -m pytest tests/ -v
```

### Run Tests with Short Output

```bash
python -m pytest tests/ -q
```

### Run a Specific Test File

```bash
python -m pytest tests/test_app.py -v
```

### Testing Areas

The test suite is organized to validate application functionality across areas such as:

- API request and response validation.
- Session management.
- Conversation handling.
- Document processing.
- Academic assistance.
- Study management.
- Quiz functionality.
- Coding assistance.
- Analytics.
- Career assistance.
- Application workflows.
- Security controls.

Report the actual results from your latest test execution when publishing the repository.

---

## 12. Current Implementation Scope

Student Copilot is currently developed as an integrated functional prototype.

| Component | Current Implementation |
|---|---|
| Backend | FastAPI |
| Frontend | HTML, CSS, JavaScript |
| Voice integration | Gnani Prisma and Timbre |
| LLM reasoning | Configurable providers |
| Offline demonstration | Mock mode |
| Document processing | PyMuPDF |
| Document retrieval | BM25 |
| Session management | In-memory |
| Opportunity records | Synthetic data |
| Application submission | Demonstration workflow |
| Database persistence | Not currently configured |
| Deployment | Local development setup |

These boundaries distinguish existing functionality from planned production capabilities.

---

## 13. Future Roadmap

Potential development improvements include:

### Infrastructure and Scalability

- PostgreSQL-based persistent storage.
- Redis-based distributed session management.
- Authentication and role-based access control.
- Production-grade document storage.
- Scalable deployment architecture.

### Advanced AI Capabilities

- Hybrid BM25 and vector retrieval.
- Cross-encoder reranking.
- Improved conversational memory.
- LangGraph-based multi-agent orchestration.
- Controlled tool-calling workflows.
- Improved intent classification.

### Evaluation and Reliability

- Retrieval evaluation datasets.
- Answer quality evaluation.
- Hallucination and factuality assessment.
- Voice latency benchmarks.
- Speech recognition quality evaluation.
- Automated integration testing.
- Monitoring and observability.

### Student Experience

- Verified external opportunity integrations.
- More personalized learning analytics.
- Improved multilingual voice experiences.
- Production-grade application integrations.
- Enhanced student progress tracking.

Future capabilities will be documented as they are implemented and validated.

---

## 14. Why Student Copilot?

Student Copilot explores a different approach to student assistance.

Instead of building separate applications for academic learning, coding, document understanding, examination preparation, and career development, it brings these workflows together through one conversational AI interface.

Its core value lies in combining:

- Multilingual voice interaction.
- Context-aware student assistance.
- Specialized AI modules.
- Configurable LLM reasoning.
- Document-based intelligence.
- Personalized academic workflows.
- Human-controlled application actions.

The objective is not simply to build another chatbot, but to explore how multiple AI capabilities can work together as a unified student companion.

---

## 15. Acknowledgements

Special acknowledgement to **Gnani.ai** for its voice AI technologies and the opportunity to explore practical applications of multilingual conversational AI through the **Great Indian AI Internship Challenge**.

---

## 16. Author

**Kunchakuri Sathwik**

B.Tech — Computer Science and Engineering (AI & ML)

**Areas of Interest**

- Artificial Intelligence
- Machine Learning
- Deep Learning
- Large Language Models
- Generative AI
- Retrieval-Augmented Generation
- AI Agents and Orchestration
- Voice AI


---

<p align="center">

### Student Copilot AI

**One Student. One Copilot. A Complete Learning Journey.**

*Making intelligent student assistance more accessible, conversational, and personalized.*

</p>
