# Agentic Legal

Agentic Legal is an AI-powered legal document analysis and review platform. It leverages multiple specialized AI agents, vector databases, and document processing tools to automate and enhance legal workflows such as risk identification, intelligent redlining, and precedent analysis.

## 🚀 Features

- **Risk Identification**: Automatically scans legal documents (e.g., contracts, policies) to identify potential risks, liabilities, and non-compliance with company guidelines.
- **Intelligent Redlining**: Generates contextual redlines and suggested revisions based on historical data and policy guardrails.
- **Precedent Analysis**: Uses semantic search over a vector database to find relevant historical precedents and standard clauses.
- **Automated Workflows**: Orchestrates complex, multi-step document review processes and maintains a rigorous audit trail of all AI-generated decisions and human modifications.
- **Robust API**: Provides RESTful endpoints to seamlessly upload documents, trigger reviews, and retrieve analysis results.

## 🏗️ Architecture

The system is built on a modular, agent-centric architecture:

- **Agents (`/agents`)**:
  - `risk_identifier.py`: Flags risky clauses and deviations from standard policies.
  - `redline_agent.py`: Proposes automated edits and alternative standard language.
  - `precedent_agent.py`: Queries past documents for consistency and context.
- **Tools (`/tools`)**:
  - `pdf_processor/`: Uses PyMuPDF to extract text, tables, and metadata from legal PDFs.
  - `vector_store/`: Integrates with Pinecone (or Weaviate) for fast, semantic search capabilities over past contracts.
  - `policy_library/`: Loads and structures the organization's legal playbooks and active policies.
- **Workflows (`/workflows`)**: Orchestrates the agents and tools to execute the end-to-end `doc_review_workflow` while seamlessly logging actions via the `audit_trail_workflow`.
- **API (`/app/api`)**: Exposes the system's capabilities to front-end applications or upstream services.

## 🛠️ Getting Started

### Prerequisites

- Python 3.10+
- Pinecone API Key (or alternative vector store)
- Relevant LLM API Keys (e.g., OpenAI, Anthropic)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YourOrg/Agentic-Legal.git
   cd Agentic-Legal
   ```

2. **Create a virtual environment:**
   ```bash
   python -m venv venv
   # On Windows:
   venv\Scripts\activate
   # On macOS/Linux:
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

### Configuration

Configure the environments in the `config/` directory:
- `config/dev.yaml` - Local development settings (default)
- `config/staging.yaml` - Staging environment setup
- `config/prod.yaml` - Production configuration

Ensure you populate your vector database credentials and LLM API keys via environment variables or securely load them into the configuration files.

### Usage

1. **Start the API Server** (assuming a FastAPI setup):
   ```bash
   uvicorn app:app --reload
   ```
2. **Upload a Document for Review**:
   Use the `/api/v1/upload_doc` endpoint to upload a sample PDF contract (e.g., from `data/sample_contracts/`) to kickoff the automated review workflow.

## 🧪 Testing

The project includes comprehensive testing to guarantee accurate agent behavior and reliable workflows.

```bash
# Run unit tests to verify individual agents and tools
pytest tests/unit

# Run end-to-end integration tests
pytest tests/integration
```

## 🤝 Contributing

Contributions are welcome! Whether you are adding new legal agents, expanding workflow capabilities, or integrating new tools, please follow the standard PR process.

## 📄 License

This project is licensed under the MIT License.
