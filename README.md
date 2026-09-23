# Mozark MCP Server

Manage test cases, generate AI-grounded test coverage, execute tests on real devices, and automate testing workflows — directly within Claude, Cursor, VS Code, or any MCP-enabled client, using plain English.

#### Test in plain English
Create test cases, run them on real devices, and manage your whole QA workflow just by describing what you want — no dashboards, no clicking through screens.

#### One workspace, everything connected
Test case management, AI test generation, real-device execution, and device automation all live behind a single MCP server — no juggling separate tools for separate steps.

#### Grounded in your real app
Upload screenshots, PRDs, and requirement docs so every AI-generated test case is grounded in what your product actually looks like and does.

[![Watch the demo](https://img.youtube.com/vi/YOUR_VIDEO_ID/maxresdefault.jpg)](https://www.youtube.com/watch?v=YOUR_VIDEO_ID)

## ⚡ One-Click Setup

Mozark is a **remote MCP server** — no Node.js, no local install, nothing to keep updated. Click a button, or point any Streamable-HTTP client at the URL below.

[![VS Code Marketplace](https://img.shields.io/visual-studio-marketplace/v/mozark-mcp.mozark-mcp?style=for-the-badge&label=VS%20Code%20Marketplace&color=0098FF&logo=visualstudiocode&logoColor=white)](https://marketplace.visualstudio.com/items?itemName=mozark-mcp.mozark-mcp)
[![Add to Cursor](https://cursor.com/deeplink/mcp-install-dark.svg)](https://cursor.com/en/install-mcp?name=mozark&config=eyJ1cmwiOiJodHRwczovL21jcC5tb3phcmsuYWkvbWNwIn0%3D)

> **Note:** the remote server (`mcp.mozark.ai/mcp`) works the same way across every supported client — no config differences to manage between them.

## 💡 Usage Examples

### 📋 Test Case Management (TCM)
Create, search, update, and organize test cases, folders, requirements, test plans, test runs, and bugs.

```
# Create test coverage
"Generate negative functional test cases for the checkout flow and save them to the Payments folder."

# Manage a test run
"Run TR-12 on a free Pixel 7 with screen recording on and record step results."

# Track bugs
"List open bugs assigned to me."
```

### 🤖 AI Test Generation
Generate functional, edge-case, or automation test cases from screenshots and requirement documents, then save them with AI-provenance tags.

```
"Generate edge-case tests for offline mode."
"Which existing cases cover guest checkout?"
"Find duplicate test cases in this project and show me what you'd merge."
```

### 📚 Knowledge Base
Upload screenshots, PRDs, BRDs, and user stories so generated tests are grounded in your real app, not guesswork.

```
"Index this PRD so future test generation understands the new checkout flow."
```

### 📱 Real-Device Execution (Optics)
Run a test case step-by-step on a real Android or iOS device, with visual verification at every step and results recorded automatically.

```
"Run TR-12 on a free Pixel 7 with screen recording on."
```

### 🔧 Device Automation (Appium)
Start raw Appium sessions on Mozark cloud devices — install your app, find and tap elements, capture screenshots and logs.

```
"Install my APK on a Pixel 7 and take a screenshot of the home screen."
```

### 🛡️ Admin Control Panel (ACP)
Look up organizations, projects, apps, users, roles, and plan usage.

```
"How much of our device-hours quota have we used this month?"
"Who has access to the Checkout project?"
```

## 🛠️ Installation

No prerequisites — Mozark is fully hosted, so there's nothing to install or keep updated locally.

### Connect your client

**Claude.ai / Claude Desktop:**
1. Open **Settings → Connectors**
2. Select **Add custom connector**
3. Name it `Mozark`, paste the server URL (`https://mcp.mozark.ai/mcp`), and select **Add**
4. Select **Connect** and complete sign-in in the browser
5. In a new chat, open the tools menu and make sure **Mozark** is toggled on

**Claude Code** — run once in a terminal:
```bash
claude mcp add --transport http mozark https://mcp.mozark.ai/mcp
```
Then run `/mcp` inside a session and choose **Mozark** to authenticate.

**Cursor** — `~/.cursor/mcp.json`:
```json
{
  "mcpServers": {
    "mozark": {
      "url": "https://mcp.mozark.ai/mcp"
    }
  }
}
```

**VS Code (Copilot):** the simplest path is installing the [Mozark extension from the VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=mozark-mcp.mozark-mcp) — it registers the server automatically, no config file needed. Alternatively, add it manually via `.vscode/mcp.json`:
```json
{
  "servers": {
    "mozark": {
      "type": "http",
      "url": "https://mcp.mozark.ai/mcp"
    }
  }
}
```

**Windsurf** — Settings → Cascade → MCP servers:
```json
{
  "mcpServers": {
    "mozark": {
      "serverUrl": "https://mcp.mozark.ai/mcp"
    }
  }
}
```

**Codex:**
```bash
codex mcp add mozark --url https://mcp.mozark.ai/mcp
```

After connecting, sign in and authorize access to your Mozark workspace. Verify with: *"Are you connected to Mozark? Show me my active context."*

## 📋 Tools by Category

137 tools across seven categories — your assistant picks the right one based on what you ask. Full reference: [docs.mozark.ai/mcp](https://docs.mozark.ai/mcp/mozark-mcp-docs/reference/tools-by-category)

**Context & Identity** — `mozark_get_active_context` · `mozark_set_active_context` · `mozark_switch_organization` · `mozark_switch_project` · `mozark_switch_app` · `whoami` · `get_workflow_rules`
*"Which project am I in?" · "Switch to the iOS app."*

**Admin Control Panel (ACP)** — `acp_list_organizations` · `acp_list_projects` · `acp_list_apps` · `acp_list_users` · `acp_get_entitlements` · `acp_get_usage_report`
*"How much of our device-hours quota have we used this month?"*

**Test Case Management (TCM)** — full CRUD on test cases, folders, requirements, test plans, test runs, and bugs (`tcm_create_test_case`, `tcm_list_test_plans`, `tcm_create_bug`, and more)
*"List open bugs assigned to me." · "Lock TR-5 so nobody edits it."*

**AI Agents** — `generate_test_cases` · `save_test_cases` · `search_test_cases` · `suggest_test_plan` · `find_duplicate_test_cases`
*"Generate edge-case tests for offline mode."*

**Knowledge Base** — `upload_document` · `process_uploaded_image` · `retrieve_from_knowledge_base` · `load_pom`

**Optics (Real-Device Execution)** — `optics_start_session` · `optics_execute_keyword` · `optics_export_yaml` · `optics_add_step_evidence`

**Appium (Device Automation)** — session, app, interaction, and evidence tools: `appium_start_session` · `appium_install_app` · `appium_find_element` · `appium_take_screenshot`, and more

## ⚠️ Notes

- Tool invocations depend on the connected LLM's interpretation of your request — results can vary slightly between clients and models.
- New tools and capabilities are added regularly; see [docs.mozark.ai/mcp](https://docs.mozark.ai/mcp) for the current reference.

## 📖 Full Documentation

See [docs.mozark.ai/mcp](https://docs.mozark.ai/mcp) for setup guides, the complete tool reference, and troubleshooting.

## License

MIT
