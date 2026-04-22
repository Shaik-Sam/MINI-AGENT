# MINI-AGENT

# Mini Agent (Windows Optimized)

**Mini Agent** is a minimal yet professional demo project that showcases the best practices for building agents with the **MiniMax M2.5 model**. Leveraging an Anthropic-compatible API, it fully supports interleaved thinking to unlock M2's powerful reasoning capabilities for long, complex tasks.

This project comes packed with features designed for a robust and intelligent agent development experience:
✅ **Full Agent Execution Loop:** A complete foundation with a toolset for file system and shell operations.
✅ **Persistent Memory:** An active **Session Note Tool** ensures the agent retains key information.
✅ **Intelligent Context Management:** Handles long-task context by summarizing conversation history.
✅ **Claude Skills Integration:** Includes 15 professional skills for documents, design, and development.
✅ **MCP Tool Integration:** Natively supports Model Context Protocol for web search and knowledge access.
✅ **Comprehensive Logging:** Detailed logs for every request and tool execution located in `~/.mini-agent/log/`.

---

## Table of Contents
1. [Get API Key](#1-get-api-key)
2. [Prerequisites & Installation](#2-prerequisites--installation)
3. [Configuration (Manual Setup)](#3-configuration-manual-setup)
4. [Usage Examples](#4-usage-examples)
5. [Troubleshooting](#5-troubleshooting)

---

## 1. Get API Key

MiniMax provides both global and China platforms. Choose based on your network environment:

| Version | Platform | API Base |
| :--- | :--- | :--- |
| **Global** | [platform.minimax.io](https://platform.minimax.io) | `https://api.minimax.io` |
| **China** | [platform.minimaxi.com](https://platform.minimaxi.com) | `https://api.minimaxi.com` |

**Steps to get API Key:**
1. Visit the platform to register and login.
2. Go to **Account Management > API Keys**.
3. Click **"Create New Key"** and save it securely.
4. **Note:** Ensure your account has a positive balance to avoid the `insufficient balance (1008)` error.

---

## 2. Prerequisites & Installation

For the most stable experience on Windows PowerShell, follow these manual installation steps:

### Install Dependencies
    Run the following command to install all necessary libraries for the multi-provider wrapper:
     ```powershell
        pip install anthropic openai tiktoken pyyaml httpx pydantic requests prompt-toolkit mcp rich
 ### Initialize Skills
Ensure the Claude Skills submodules are downloaded to enable professional document and design capabilities:

    ```powershell
     git submodule update --init --recursive

### 3. Configuration (Manual Setup)
The agent looks for configuration in specific priority paths. For our execution, we use the **Global User Directory** to ensure the agent can access settings from any workspace.

#### **Step A: Create the config directory**
    ```powershell
         mkdir -p C:\Users\$env:USERNAME\.mini-agent\config

#### **Step B: Copy the template**
Run the following command to move the template into your global user configuration folder:

    ```powershell
       cp mini_agent/config/config-example.yaml C:\Users\$env:USERNAME\.mini-agent\config\config.yaml
 
#### **Step C: Edit the file**
Open the new `config.yaml` file in VS Code and replace the placeholders with your actual API credentials. Ensure the indentation matches this format:

    ```yaml
      api_key: "YOUR_MINIMAX_API_KEY"
     api_base: "[https://api.minimax.io](https://api.minimax.io)"
     model: "MiniMax-M2.5"
     provider: "anthropic"
4. Usage Examples
Starting the Agent
To ensure all relative paths and module imports work correctly, navigate to the project root and run the CLI module directly via Python:
   ```powershell
         cd Mini-Agent
          python -m mini_agent.cli

### Task Execution Demo
 Once you see the mini-agent> prompt, paste the following command. This demo highlights the agent’s ability to perform environment checks, file creation, and code execution in a single reasoning loop:

   ```powershell
   "Check if there is a file named 'test.txt' in my workspace. If not, create it with the text 'Mini-Agent is live'. Then, write a short Python script that prints the current date and time, and run it   using the shell tool."


