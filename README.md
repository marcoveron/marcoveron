# Marco Verón

Security engineer building AI-assisted tooling for SOC teams: agents that triage alerts, enrich indicators and propose responses, with a human approving anything that touches the network.

Asunción, Paraguay · Final-year Computer Engineering student (program taught in English; exchange at NTUST, Taipei)

## What I build

- **LLM agents for security operations.** Tool-using agents that work over SIEM data (Wazuh / OpenSearch) and map what they see to MITRE ATT&CK.
- **Guardrails for those agents.** Human-in-the-loop approval, dry-run modes and append-only audit trails. An agent that can block an IP needs a gate it cannot skip.
- **SOC automation.** Triage workflows in n8n, detection logic with Sigma and YARA, and the Python that ties it together.

## Featured

### [wazuh-mcp](https://github.com/marcoveron/wazuh-mcp)
An MCP server that gives models access to a Wazuh deployment: agent inventory, alert hunting, vulnerabilities, configuration assessment and Active Response.

- One response shape across every tool, with honest totals (it flags when the Indexer stopped counting instead of reporting a capped number as exact).
- Aggregation tools so a model answers "what happened last night" in one call instead of paging through hundreds of alerts.
- Write tools are not even registered unless explicitly enabled, with a command allowlist and a guard against fleet-wide actions.
- Built-in SOC workflows as MCP prompts (shift briefing, alert triage, host investigation, hunting) and 92 tests that run without a Wazuh instance.

### [soc-analyst-llm-wazuh](https://github.com/marcoveron/soc-analyst-llm-wazuh)
A local-LLM SOC analyst that reads Wazuh alerts, reasons about them and proposes active responses: block an IP, isolate a host, kill a process.

- Runs fully on-premise with Ollama (`llama3.1:8b`), so no alert data leaves the network.
- Every state-changing action pauses the LangGraph agent with an `interrupt` until an operator clicks Authorize or Deny in the Streamlit UI.
- Tools for alert retrieval, IP reputation (local Wazuh evidence plus AbuseIPDB), indicator enrichment (VirusTotal), fleet status and incident reports.
- Each decision is written to an append-only audit log.

## Stack

- **Security:** Wazuh · Suricata · OpenSearch · MITRE ATT&CK · Sigma · YARA
- **AI:** LangChain · LangGraph · Ollama · MCP
- **Engineering:** Python · FastAPI · PostgreSQL · Docker · Linux · n8n

## Also built

An ESP32 fall-detection wearable that classifies motion in real time with TinyML (Edge Impulse).

## Currently exploring

LLM gateways and how to secure the LLM applications that sit behind them.
