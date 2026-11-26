# AI Career & Skill Intelligence Platform

An AI-powered career development platform that helps students, freshers, and working professionals understand their demonstrated skills, identify gaps for a target role, practice deliberately, and measure progress toward career readiness.

> **Project status:** Foundation setup in progress. A Django project scaffold and backend dependency list are present. The React frontend scaffold is pending Node.js/npm setup. Product features have not yet been implemented.

## Product Vision

People often study technologies and prepare for jobs without a clear picture of what they can demonstrate, what they need to improve, or what to learn next. This platform will use ongoing assessments and evidence of performance to build that picture and guide the user toward a chosen career role.

The product is intended to be more than a course catalog or a general-purpose chatbot. Its core cycle is:

**Assess -> Identify skill gaps -> Learn -> Practice -> Evaluate -> Track improvement -> Build career readiness**

The platform should help users answer:

- What skills can I currently demonstrate?
- Which skills are below the level expected for my target role?
- Is my knowledge improving over time?
- What should I focus on next?
- Does my resume reflect evidence of my skills?

Demonstrated skill levels must be grounded in assessment evidence. Completing a course or marking a task complete is not, by itself, evidence that a skill score should increase.

## Initial MVP

Build the product incrementally, milestone by milestone. The initial MVP is expected to include:

1. User registration and login.
2. User profile and career role selection.
3. Configurable, role-specific skill frameworks.
4. An initial skill assessment and skill-wise scoring.
5. Skill gap analysis against a selected target role.
6. A personalized learning plan, including daily activities.
7. Daily assessments and practice.
8. A basic progress dashboard.
9. AI-generated explanations, feedback, and recommendations.

The MVP is a starting boundary, not a requirement to build all capabilities at once. Each capability should be delivered and documented in a small, reviewable milestone.

## Planned Technology Stack

| Area | Planned technology |
| --- | --- |
| Frontend | React, TypeScript, Vite, React Router, reusable components and React Hooks |
| API communication | Axios through a centralized frontend API client |
| Styling | CSS or a modular styling approach; add libraries only when justified |
| Backend | Python, Django, Django REST Framework, and Django ORM |
| Database | PostgreSQL with Django ORM migrations, relational constraints, and appropriate indexes |
| Assessment and AI | Deterministic Python assessment/scoring algorithms plus a dedicated external LLM service layer |
| Version control | Git and GitHub, with feature branches where useful and small, meaningful commits |

The AI integration should use structured outputs and separately maintained prompt templates. Keep provider-specific details behind a service boundary so that business logic does not depend on a particular LLM vendor. Future options may include open-weight models, retrieval-augmented generation (RAG), LoRA/QLoRA fine-tuning, and speech assessment.

## Product Roadmap

The roadmap is ordered to establish a reliable foundation before adding more advanced capabilities. Phases may be refined as requirements and implementation evidence develop.

| Phase | Planned scope |
| --- | --- |
| 1. Project foundation | Verify the development environment; initialize frontend and backend; configure PostgreSQL and React/Django integration; manage environment variables; establish Git conventions and project documentation. |
| 2. Authentication and user management | Registration, login/logout, authentication, profile, education, experience, existing skills, and career interests. |
| 3. Career roles and skills | Start with Python Developer, AI/ML Engineer, and Data Analyst roles. Store configurable skill requirements in the database rather than scattering role-specific rules through application code. |
| 4. Initial skill assessment | Question bank, MCQs, technical tests, practical coding exercises, difficulty levels, answer evaluation, assessment attempts, skill-wise scores, and an initial skill baseline. |
| 5. Skill gap analysis | Compare demonstrated levels with target-role requirements; identify strengths, weak and missing skills; prioritize improvement areas; produce a gap report. |
| 6. Personalized learning roadmap | Recommend topics, exercises, and resources; create daily tasks and weekly plans; prioritize gaps and adapt future plans to assessment results. |
| 7. Daily practice and assessment | Daily quizzes and practical exercises, answer evaluation, AI explanations, mistake analysis, and reassessment. |
| 8. Progress tracking and analytics | Show initial and latest scores, historical skill performance, weekly/monthly progress, improvement charts, and remaining gaps. Only assessment evidence changes demonstrated skill levels. |
| 9. AI career coach | Explain incorrect answers, suggest next learning steps and projects, answer career questions, and provide personalized feedback. |
| 10. Resume and career readiness | Resume upload and analysis, missing-skill identification, improvement suggestions, project recommendations, readiness reports, and resume generation/revision history. |

### Future possibilities (outside the initial MVP)

- LeetCode-style coding platform and advanced code execution environment.
- Voice-based communication assessment and AI mock interviews.
- Advanced resume automation and job matching.
- College placement and enterprise dashboards.
- Custom fine-tuned language models.

These are possible later directions, not commitments for the first release.

## Initial Role and Skill Framework

The first role catalog is planned to cover three target roles. Skills and role requirements should be maintainable as data and configurable over time.

| Target role | Example skill areas |
| --- | --- |
| Python Developer | Python fundamentals, object-oriented programming, advanced Python, SQL, Django, REST APIs, data structures and algorithms, Git, testing, communication, and problem solving. |
| AI/ML Engineer | Python, mathematics and statistics, machine learning, deep learning, PyTorch, computer vision, generative AI, RAG, and deployment. |
| Data Analyst | Python, SQL, Excel, statistics, data cleaning, data visualization, and Power BI or equivalent tools. |

This is an initial skill outline, not a final assessment rubric. Skill definitions, proficiency expectations, and scoring rubrics should be refined and reviewed as the product develops.

## Architecture and Engineering Principles

### Frontend

- Organize code by product feature.
- Keep pages, reusable components, hooks, services, and types clearly separated.
- Centralize API configuration and route configuration.
- Keep business logic out of UI components where practical.
- Use type-safe interfaces, focused components, and avoid unnecessary duplication.

### Backend

- Organize Django applications around business domains.
- Separate data models from business operations.
- Use serializers for API validation and representation; keep views thin.
- Put business rules in service modules or classes where appropriate.
- Organize URLs clearly, use reusable utilities, and centralize exception handling where it helps.
- Model relationships and constraints deliberately; add indexes where query patterns require them.
- Avoid abstractions that do not solve a real problem.

### Across the project

- Prefer readable, maintainable code and meaningful names.
- Give modules, components, and functions a clear responsibility.
- Reuse components and services when that reduces duplication.
- Keep files focused and reasonably sized.
- Comment on non-obvious decisions, not self-explanatory code.
- Follow ecosystem conventions and add dependencies only when justified.
- Do not over-engineer; preserve a clear path for future changes.

### Assessment and AI boundaries

- Use deterministic, reviewable logic for assessment scoring where possible.
- Treat the LLM as a provider-backed service for explanations and recommendations, with structured outputs and validated results.
- Keep prompts separately maintained and do not let generated prose silently alter assessment scores.
- Base demonstrated skill levels on assessment evidence; learning activity completion alone does not raise scores.
- Evaluate AI output quality and assessment consistency, and review scoring rubrics with humans.

## Planned Directory Structure

This layout is being created milestone by milestone. The Django project scaffold is present under `backend/`; `frontend/` is reserved for the Vite app once Node.js/npm are available. The `docs/` directory remains planned.

```text
AI-Career-Intelligence/
|-- frontend/                 # React + TypeScript application (scaffold pending)
|-- backend/
|   |-- config/                # Django project configuration
|   `-- manage.py
|-- docs/                     # Requirements and technical documentation (planned)
|-- .gitignore
|-- requirements.txt          # Python backend dependencies
`-- README.md
```

The frontend and backend structures will be expanded when those projects are initialized. No application layout is prescribed before the relevant design work.

## Documentation Strategy

Documentation is part of delivery. The following files are planned; aside from this README, they are not created as part of this initial documentation task.

| Document | Purpose |
| --- | --- |
| `README.md` | Overall vision, stack, architecture principles, roadmap, and development guidance. |
| `docs/PROJECT_REQUIREMENTS.md` | Product and functional requirements. |
| `docs/TECHNICAL_ARCHITECTURE.md` | System architecture and technical decisions. |
| `docs/DATABASE_DESIGN.md` | Database entities, relationships, constraints, and indexing decisions. |
| `docs/API_DOCUMENTATION.md` | API endpoints and request/response structures. |
| `docs/DEVELOPMENT_PROGRESS.md` | Completed, ongoing, and upcoming milestones. |
| `docs/CHANGELOG.md` | Important changes and feature history. |

When implementing a feature, update the relevant requirements, architecture, API, and database documents as applicable. Update development progress for each milestone and record important changes in the changelog. Describe a feature as complete only after it has actually been implemented and verified.

## Development Workflow and Learning

Work in small milestones so the product remains understandable and reviewable. For each milestone:

1. Explain the intended outcome and the concepts involved.
2. Identify the files expected to be created or changed.
3. Implement the scoped functionality using the documented architecture.
4. Explain the implementation and key design decisions.
5. Run appropriate checks and tests, then review the changes.
6. Update the relevant documentation and progress record.
7. Provide a suggested Git commit command.

The goal is to learn while building. Future implementation work should begin by reading this README and relevant project documentation, then inspecting the actual codebase rather than assuming what exists.

### Git conventions

- Use feature-based branches where appropriate.
- Prefer small commits with one clear purpose.
- Use meaningful commit messages, for example:
  - `feat: initialize React TypeScript frontend`
  - `feat: configure Django REST backend`
  - `feat: integrate PostgreSQL database`
  - `feat: implement user authentication`
- A suggested commit command may be provided after a milestone. Do not run `git commit`, `git push`, or destructive Git operations without explicit approval.

## Security and Configuration

- Store secrets and environment-specific configuration in environment variables.
- Never expose API keys in frontend code or commit `.env` files.
- Maintain `.env.example` files that document required variable names without real secrets.
- Use Django password hashing and appropriate authentication mechanisms.
- Validate API input and apply permission checks to every user-specific operation.
- Protect user data and avoid collecting or retaining sensitive personal information without a clear need.
- Configure CORS for known application origins, and use HTTPS in production.
- Handle uploaded resumes and other files with secure storage and access controls when that feature is implemented.

## Testing and Quality Expectations

Testing should match the risk and scope of each feature. A feature is not complete merely because the application starts or code executes.

| Area | Expected checks |
| --- | --- |
| Frontend | TypeScript type checking, component tests where appropriate, API integration tests, and build verification. |
| Backend | Django tests, API tests, serializer validation tests, service-layer tests, and database integration tests. |
| AI and assessment | Evaluation datasets, structured-output validation, assessment consistency checks, output quality and hallucination checks, and human review of scoring rubrics. |

## Development Environment

The developer manages Python, Node.js and npm, PostgreSQL, Git, and VS Code. Python 3.15 and Git are available in the current environment, and the project virtual environment contains Django plus the backend packages listed in `requirements.txt`. Node.js/npm were unavailable; the official Node.js installer could not complete, so install Node.js LTS and npm before creating the Vite frontend. PostgreSQL availability and configuration still need to be checked before database integration.

The initial Django project and backend Python dependencies have been set up. PostgreSQL, frontend dependencies, and application features remain unconfigured.

## Deployment Direction

Deployment is not part of the initial project initialization. Later options may include:

- Frontend on Vercel or another suitable hosting provider.
- Backend on AWS or another suitable cloud provider.
- Managed PostgreSQL.
- Secure cloud object storage for uploaded files.
- An external LLM API initially, with optional self-hosted models later.
- A configured domain and HTTPS for production.

Deployment choices should be revisited when the application requirements and operational needs are clearer.

## Recommended Next Milestone

Complete **Phase 1: Project Foundation** by installing Node.js LTS/npm, creating the React + TypeScript + Vite app in `frontend/`, checking PostgreSQL availability, and then configuring backend/frontend local integration and environment-variable conventions. Record the decisions in the planned documentation before starting feature implementation.

