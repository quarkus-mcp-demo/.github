# MCP Servers for Developers: A Demo with Quarkus, Keycloak, ContextForge

## Overview
This repository contains a real-world demonstration illustrating how to build and deploy Model Context Protocol (MCP) servers in an enterprise environment. 

The demo focuses on securely integrating a customer support AI agent (named "Glo") into an e-commerce platform called "Globex". 

This demo show how MCP servers sit between your agent and your enterprise systems, help you to define endpoints called Tools that your agent can discover and access. So instead of an agent ‘figuring out’ how to interact with your backend, it operates within this intentional toolbox. Basically MCP makes APIs consumable by agents.

By exploring this repository, developers can learn how to implement strict security boundaries, prevent the AI from handling sensitive user credentials, and expose only minimal, intent-driven tools to the language model.

## Key Features & Architectural Patterns
* **Enterprise Tech Stack:** Built with Quarkus, LangChain4j, LangGraph4j, Keycloak, and ContextForge, running on Red Hat OpenShift. The wider project includes microservices like `globex-store` (Java), `globex-store-db` (Python), and `globex-web` (TypeScript).
* **Brownfield & Greenfield Deployments:** Demonstrates how to build a standalone "Brownfield" MCP server to act as a control layer in front of an existing legacy API (Order History), as well as a "Greenfield" pattern where the MCP server and API are co-located in the same application (Customer Complaints).
* **Identity & Authentication Guardrails:** Integrates external and internal Keycloak realms for robust identity management. Instead of passing sensitive user data in agent tool arguments, the architecture uses OIDC, service account flows, and token exchanges so the backend API can identify the user securely.
* **MCP Gateway:** Showcases an MCP Gateway to manage internal and external server sprawl, aggregate connections behind a single endpoint, handle observability, and connect external tools like Jira for internal product managers.

## Setup

To set up and run the demo, please follow these steps:

1. `git clone https://github.com/quarkus-mcp-demo/mcp-demo-poc`
2. Make a copy of `install/ansible/inventories/inventory.template` and save as `inventory`. Update `inventory` with the keys needed.
3. `cd install/ansible`
4. `ansible-playbook playbooks/ocp4_workload_mcp_demo_poc.yml -i inventories/inventory`

## Resources

1. Token Exchange Setup: https://quarkus.io/blog/secure-mcp-oidc-client/
2. IBM's opensource MCP Gateway ContextForge: https://ibm.github.io/mcp-context-forge


Disclaimer: Written with support of NotebookLM
