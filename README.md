# AI-Powered Shipment Disruption Router

A notebook-based shipment disruption workflow using LangGraph, LangChain,
OpenAI, and policy retrieval through Hugging Face embeddings and Chroma.
It includes classification, routing, validation, human-in-the-loop escalation,
and evaluation against curated test cases.

## Project files

- [Notebook](AI_Powered_Shipment_Disruption_Router.ipynb): workflow and evaluation.
- [Policy rulebook](logistics_policy_rulebook.txt): shipment handling policies.
- [Test cases](test_cases_curated.csv): curated inputs and expected decisions.
- [Configuration template](config.example.json): local API settings.
- [Dependencies](requirements.txt): Python packages.

## Setup on Windows

Use Python 3.12 and the VS Code Python and Jupyter extensions.
From the repository directory, run:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
Copy-Item config.example.json config.json
```

Edit `config.json` locally to add your OpenAI API key. To enable LangSmith
tracing and its dashboard, also supply a LangSmith API key and change
`LANGCHAIN_TRACING_V2` to `"true"`.
Open the notebook, select the `.venv` Python kernel, and run cells in order
with the repository directory as the working directory.

The first embedding run may download `sentence-transformers/all-MiniLM-L6-v2`.
The import cell sets `USE_TF=0` before loading the embedding stack so it uses
PyTorch without importing optional TensorFlow dependencies. Restart the kernel
after changing this setting or installing packages.

OpenAI calls may incur charges. Workflow content is sent to the configured
OpenAI endpoint; enabling LangSmith also sends tracing data to LangSmith.
Use only data you are authorized to send.

## Publishing and provenance

The public notebook has execution outputs and execution counts cleared.
Credentials, generated vector databases, unrelated notebooks, and course PDFs
are excluded. Never commit your local `config.json` or API keys. Clear notebook
outputs again before committing future runs.

The notebook retains its original educational content and attribution.
No new license is granted for third-party course materials.