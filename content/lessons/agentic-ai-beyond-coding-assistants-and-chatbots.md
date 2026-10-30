+++
title = "Agentic AI: Beyond Coding Assistants and Chatbots"
description = "Hands-on workshop on building AI agents step by step, from a plain OpenAI REST API call to multi-agent workflows in Pydantic AI, with models served by the Aitta inference service on LUMI."

[taxonomies]
skill = ["ai", "agentic", "gen_ai", "programming", "hpc"]
difficulty = ["intermediate"]
maturity = ["beta"]

[extra]
tags = ["pydantic-ai", "mcp", "tool-calling", "memory", "skills", "aitta", "lumi", "workshop"]
external_url = "https://learn.swedenaifactory.se/agentic-ai-lesson/"
+++

{{ <external/> }}

This hands-on workshop, organized by **LUMI AI Factory** and **Sweden AI Factory**, teaches you to build AI agents that can act, not just answer. We build agents in stages, starting with a plain OpenAI REST API call and ending with multi-agent workflows in Pydantic AI. The models run on the LUMI supercomputer and are served by the Aitta inference service. Our running example is a flight-booking assistant.

## Overview

- **LLM basics and inference**: how models work at a practical level, serving models with the Aitta inference server, and using prompt templates.
- **Building agents from scratch**: from a single REST call to structured agentic workflows with Pydantic AI.
- **Components of an agent**: the model, the harness, the loop, tools, MCP servers, skills, memory, and how they fit together.
- **Security and evaluation**: what breaks when agents leave the laptop, how to evaluate them, and how to run them reliably.

## Key takeaways

- Identify the main components of an AI agent (model, tools, memory, harness) and recall standard concepts such as tool calling and MCP.
- Build working agents in stages, from a raw OpenAI REST API call to structured agents with Pydantic AI, and connect tools, MCP servers and memory to them.
- Analyze and identify potential pitfalls when moving agents from development to production.

## Who is this for?

- IT professionals, software engineers and data scientists
- Programmers curious to move out of a chat interface and integrate AI in their routine tasks
- People who have used LLM chatbots or coding assistants and want to understand how they work behind the scenes

## Prerequisites

- Prior programming experience in Python; no machine learning background is needed
- Basic use of a terminal and a code editor
- A LUMI account that is a member of any LUMI project, used to log in to Aitta
