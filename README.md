# Morathi-Academic: Full RAG Azure Functions (GitHub-ready)

This repository contains a full Retrieval-Augmented Generation backend implemented as Azure Functions (Linux, Python 3.12).
Functions included:
- orchestrator
- retriever
- summarizer
- quality_rater
- report_generator
- pdf_generator
- verifier
- planner
- memory (simple stub)
- shared/ helpers

## Deployment
1. Push this repo to GitHub (root must contain host.json and requirements.txt).
2. Add GitHub Secrets:
   - `AZURE_FUNCTIONAPP_NAME` - your Function App name
   - `AZURE_FUNCTIONAPP_PUBLISH_PROFILE` - publish profile XML (from Azure portal)
3. In Azure Portal: Function App -> Configuration set required app settings:
   - `AzureWebJobsStorage` (required)
   - `AZURE_OPENAI_ENDPOINT`, `AZURE_OPENAI_KEY`, `AZURE_OPENAI_DEPLOYMENT` (optional for LLM summaries)
   - `SEMANTIC_SCHOLAR_URL` (optional)
4. Push to `main` to trigger GitHub Actions deployment.
5. Test the orchestrator endpoint:
   POST /api/orchestrator with JSON `{ "query": "transformer models in NLP", "limit": 5 }`
