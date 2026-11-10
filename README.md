# Student Copilot AI — Complete Product Blueprint Implementation

> **Submission for the Gnani.ai Great Indian AI Internship Challenge**  
> *One student profile, one continuous conversation, 12 intelligent capabilities.*  
> All opportunity listings, student profiles, and application portals are **synthetic** for student safety and DPDP compliance.

---

Student Copilot AI is a voice-first, multilingual AI companion designed for Indian engineering students who think in Telugu or Hindi but study and code in English. Instead of juggling separate apps for doubts, notes, syllabus tracking, coding errors, interview prep, scholarships, internships, and resumes, students speak to one unified AI copilot.

---

## 12-Module Feature Architecture

| # | System Module | Status | Core Capabilities |
|---|---|---|---|
| **M1** | **Voice Intelligence** | ✅ Active | Push-to-talk, Telugu/Hindi/English code-mixing, Gnani Prisma STT (`/stt/v3`), Gnani Timbre TTS (`/api/v1/tts/inference`, Vasudha v3.0 → Varuni v2.5 fallback), wake-word detection, browser Web Speech fallback |
| **M2** | **AI Doubt Solver** | ✅ Active | 5 progressive explanation levels (Level 1: simple to Level 5: implementation), misconception detection, Telugu-English style adaptation, image-based doubt solving (`/api/doubts/image` with Gemini multimodal) |
| **M3** | **Learning Assistant** | ✅ Active | Prerequisite identification, adaptive depth adjustments, interactive concept checks, multi-mode teaching |
| **M4** | **Document Intelligence** | ✅ Active | PDF parsing via PyMuPDF, BM25 retrieval with page citations `[p.N]`, multi-style notes generation (`short`, `detailed`, `flashcards`, `formula`, `exam`) |
| **M5** | **Exam Preparation** | ✅ Active | Interactive quiz engine, syllabus PDF tracker (`/api/exam/syllabus`) with interactive checklists, recurring question paper topic analyzer (`/api/exam/papers`) |
| **M6** | **Study Manager** | ✅ Active | Task and assignment manager, revision timetable generator, Today's Focus daily digest (`/api/today`), schedule auto-rescheduler for missed days (`/api/study/reschedule`) |
| **M7** | **Coding Mentor** | ✅ Active | Multi-language code + error explainer (Python, Java, C, C++, JavaScript, SQL, TypeScript), DSA hint-first mode (`/api/code/dsa-hint`) with 3 hint levels (no direct spoilers) |
| **M8** | **Project Assistant** | ✅ Active | Profile-based project idea generator (`/api/projects/ideas`), hackathon discovery and eligibility matching |
| **M9** | **Opportunity Finder** | ✅ Active | 8 categories (internships, scholarships, hackathons, exams, jobs, admissions, services, courses), eligibility auto-check, required fields diff (`/api/opportunities/{id}`) |
| **M10** | **Application Agent** | ✅ Active | Transparent field collection, review summary, user-only consent gate, 5-minute cryptographic one-time token (`/api/applications/confirm`) |
| **M11** | **Career Assistant** | ✅ Active | Target role skill gap analyzer (`/api/career/skill-gap`), tailored resume tips (`/api/career/resume-tips`), mock interview simulator with real-time feedback (HR, Technical, ML, SQL, DSA), portfolio advice (GitHub, LinkedIn, Blog) |
| **M12** | **Student Intelligence** | ✅ Active | Learning streak & weak topics analytics (`/api/analytics`), personalized multi-week learning roadmaps (`/api/learn/path`), Telugu-English technical term explainer (`/api/learn/term`), context-aware intent router |

---

## Quickstart

### 1. Setup Virtual Environment
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements-dev.txt
```

### 2. Configure Environment (`.env`)
Copy `.env.example` to `.env`:
```powershell
copy .env.example .env
```

To run in **Offline / Mock Mode** (no keys required, all 12 modules use high-fidelity synthetic responses):
```dotenv
MOCK_MODE=true
```

To enable **Live Gnani Voice + Free GroqCloud Reasoning**:
```dotenv
MOCK_MODE=false
GNANI_API_KEY=your_key_from_gnani_dashboard
GNANI_BASE_URL=https://api.vachana.ai

LLM_PROVIDER=groq
GROQ_API_KEY=gsk_your_groq_api_key_from_console_groq_com
GROQ_MODEL=llama-3.3-70b-versatile
```

To enable **Live Gnani Voice + Gemini Reasoning**:
```dotenv
MOCK_MODE=false
GNANI_API_KEY=your_key_from_gnani_dashboard
GNANI_BASE_URL=https://api.vachana.ai

LLM_PROVIDER=gemini
LLM_MODEL=gemini-2.0-flash
GEMINI_API_KEY=your_gemini_api_key
```

### 3. Run Server
```powershell
python -m uvicorn app:app --reload --port 8000
```
Open [http://localhost:8000](http://localhost:8000) in your browser.

---

## Gnani Model Integration

| Layer | Service | Model / Configuration | Endpoint |
|---|---|---|---|
| **STT** | Gnani Prisma | v3.0, `language_code=te-IN,en-IN`, `format=transcribe` | `POST /stt/v3` |
| **TTS** | Gnani Timbre | v3.0 Vasudha voice (`gender=female`, `speed=1.0`) with v2.5 Varuni fallback | `POST /api/v1/tts/inference` |
| **Concurrency** | Async Semaphore | `asyncio.Semaphore(1)` ensures sequential speech generation without rate spikes | In-process |
| **Audio Safety** | In-Memory Streaming | Audio is buffered in-memory and never persisted to disk (DPDP compliance) | Native |

> **Note on Evon:** Gnani Evon is an open-weights LLM and is not hosted as an API endpoint on `api.gnani.ai`. Reasoning and multimodal vision are powered by Gemini 2.0 Flash / Anthropic Claude / local fallback.

---

## Automated Test Suite

Run the full 53-test suite covering all 12 modules:
```powershell
python -m pytest tests/ -v
```

```
tests/test_all_12_modules.py .... (18 passed)
tests/test_app.py ........... (17 passed)
tests/test_new_features.py .. (18 passed)
======================== 53 passed in ~2s ========================
```

---

## Complete API Surface (55 Endpoints)

| Route | HTTP | Module | Description |
|---|---|---|---|
| `/` | GET | Core | Single Page Application UI (9 active views) |
| `/api/health` | GET | Core | Basic service health |
| `/api/health/detailed` | GET | Core | Detailed health status of all 12 modules |
| `/api/session` | POST | Core | Initialize isolated student session |
| `/api/session/{id}` | DELETE | Core | Clear session, memory, and uploaded notes |
| `/api/profile` | GET/PUT | Core | Student academic profile (in-memory) |
| `/api/turn` | POST | M1, M2, M3 | Conversational turn with language & intent routing |
| `/api/turn/audio` | POST | M1 | End-to-end voice turn (Gnani STT → Copilot → Gnani TTS) |
| `/api/transcribe` | POST | M1 | Audio to text via Gnani Prisma |
| `/api/tts` | POST | M1 | Text to speech via Gnani Timbre |
| `/api/conversation/clear` | POST | M2 | Reset chat depth & conversation context |
| `/api/doubts/image` | POST | M2 | Photo doubt extraction (textbook, board, code error) |
| `/api/documents` | POST/DELETE | M4 | Upload PDF study notes / purge from session |
| `/api/documents/notes` | POST | M4 | Generate notes (short, detailed, flashcards, formula, exam) |
| `/api/exam/syllabus` | POST/GET | M5 | Upload syllabus PDF & retrieve structured topic checklist |
| `/api/exam/syllabus/topic`| PATCH | M5 | Toggle topic completed status in syllabus |
| `/api/exam/papers` | POST | M5 | Previous year question paper analyzer & keyword extractor |
| `/api/quiz/start` | POST | M5 | Start topic-based interactive quiz |
| `/api/quiz/answer` | POST | M5 | Submit quiz answer with instant explanation |
| `/api/quiz/history` | GET | M5 | Quiz scores and weak topic history |
| `/api/study/plan` | POST/GET | M6 | Generate exam revision plan |
| `/api/study/reschedule` | POST | M6 | Redistribute remaining topics after missed study days |
| `/api/tasks` | GET/POST | M6 | Manage assignments and deadlines |
| `/api/tasks/{id}` | PATCH/DEL | M6 | Mark tasks done or remove them |
| `/api/today` | GET | M6 | Today's Focus daily summary |
| `/api/code/explain` | POST | M7 | Multi-language code debugging & conceptual explanation |
| `/api/code/dsa-hint` | POST | M7 | LeetCode/DSA hint mode (Levels 1–3, no full code spoilers) |
| `/api/projects/ideas` | POST | M8 | Tailored project ideas based on student skills and goals |
| `/api/opportunities` | GET | M9 | Filter synthetic internships, scholarships, and hackathons |
| `/api/opportunities/{id}` | GET | M9 | Opportunity details, missing eligibility fields diff |
| `/api/applications/start` | POST | M10 | Start application & receive missing requirements |
| `/api/applications/answer`| POST | M10 | Supply individual required field |
| `/api/applications/confirm`| POST | M10 | Submit application using 5-minute single-use token |
| `/api/career/skill-gap` | POST | M11 | Match existing skills against target career role |
| `/api/career/resume-tips` | POST | M11 | Actionable resume bullet points based on profile |
| `/api/career/interview/start` | POST | M11 | Launch mock interview (HR, Tech, ML, SQL, DSA) |
| `/api/career/interview/answer`| POST | M11 | Score answer & generate model response |
| `/api/career/portfolio` | POST | M11 | Profile advice for GitHub, LinkedIn, Website, or Dev Blog |
| `/api/analytics` | GET | M12 | Weak topics, study streak, quiz scores & module usage |
| `/api/learn/path` | POST | M12 | Multi-week week-by-week learning roadmap |
| `/api/learn/term` | GET | M12 | Telugu-English conversational explanation of technical terms |
| `/api/track/activity` | POST | M12 | Heartbeat to increment daily study streak |

---

## Security, Privacy & Ethics

1. **Synthetic Data Only**: All internships, scholarships, companies, and application confirmations are completely synthetic. No student PII (real phone numbers, Aadhaar, PAN) is collected or stored.
2. **Audio Privacy**: Audio streams are processed strictly in RAM and never written to disk or logged. Meets the Indian Digital Personal Data Protection (DPDP) Act standards.
3. **Application Consent Gate**: The AI agent cannot automatically submit applications on behalf of students. Submission mandates an explicit, cryptographically random one-time confirmation token with a 5-minute TTL.
4. **Content Security Policy**: Strict headers prevent inline script injection, frame-jacking (`frame-ancestors 'none'`), MIME confusion (`nosniff`), and unauthorized microphone access (`Permissions-Policy: microphone=(self)`).
5. **No CAPTCHA / Auth Bypasses**: The copilot strictly obeys host system boundaries and hands control back to the user whenever interactive verification is required.

---

## Project Structure

```
gnani ai/
├── app.py                      # FastAPI backend with all 12 modules (2,440 lines, 55 routes)
├── requirements.txt            # Production runtime dependencies
├── requirements-dev.txt        # Development & testing dependencies
├── pytest.ini                  # Pytest runner configuration
├── .env.example                # Sample environment configuration
├── static/
│   ├── index.html              # Modern responsive SPA (9 views)
│   ├── styles.css              # Custom design system with light/dark accents
│   ├── app.js                  # Frontend state, audio recorder, UI handlers
│   └── favicon.svg             # Application brand mark
├── tests/
│   ├── test_app.py             # Core security, session, tutor, and document tests
│   ├── test_new_features.py    # Code mentor, analytics, mock interview tests
│   └── test_all_12_modules.py  # Comprehensive end-to-end suite for all 12 modules
└── README.md                   # Complete architectural and operational documentation
```
