# Regulatory Tracker - Technical Architecture Documentation

**Source**: repository/technical-specifications/regulatory-tracker-technical-architecture.md
**Type**: Technical Specification
**Upload Date**: 2026-02-09
**Source SHA**: Not provided

## Key Points

- Three-tier architecture (client, frontend, backend) with asynchronous background processing for AI-powered regulatory compliance analysis using Claude API
- Frontend built with Next.js 14, React 19, TypeScript, and Tailwind CSS; backend uses FastAPI with Python 3.11+ and SQLite database
- Seven-stage scan orchestration pipeline: Initializing → Retrieving Sources → Detecting Changes → Analyzing → Scoring → Generating Artifacts → Finalizing
- Change detection leverages SHA-256 content hashing and regex-based keyword matching; scoring and analysis performed by Claude Sonnet 4 AI model
- Generates professional documentation artifacts in both Markdown (database storage) and Word (.docx) formats with metadata and structured analysis
- Background task processing via Python asyncio; deployment containerized with Docker Compose for frontend and backend services
- Includes comprehensive security, scalability, monitoring, and production deployment considerations with migration paths to PostgreSQL and distributed task queues

## Entities and Topics

- **Next.js 14**: React framework with App Router for frontend development and file-based routing structure
- **FastAPI**: Python web framework handling RESTful API endpoints for scan, results, workflow, and knowledge store management
- **Claude Sonnet 4**: Anthropic's AI model used for regulatory document analysis with configurable temperature and token limits
- **ScanOrchestrator**: Core service managing seven-stage pipeline with state transitions, error handling, and real-time status updates
- **ChangeDetectionService**: Identifies material regulatory changes using content hashing (SHA-256) and keyword pattern matching
- **ArtifactGenerator**: Creates professional documentation outputs in Markdown and Word formats with styling and metadata
- **LLMService**: Integrates Claude API with prompt engineering, output schema validation, and error handling with retry logic
- **SQLite Database**: File-based relational database storing scans, results, and source registry with schema for tracking workflow status
- **Mock Sources Directory**: JSON files simulating regulatory agency data (FinCEN, OCC, Federal Reserve) for development and testing
- **Docker Compose**: Orchestrates containerized frontend (Node.js 20) and backend (Python 3.11) services with volume management
- **Asyncio Task Queue**: Asynchronous processing framework for background scan execution with task lifecycle management

## Relevance to Project

This technical architecture document serves as the foundational blueprint for implementing the Regulatory Tracker system, detailing all technical components, data flows, API contracts, and deployment strategy necessary for building a production-ready AI-powered regulatory compliance analysis platform.