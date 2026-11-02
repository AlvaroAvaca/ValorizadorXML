# EIDEN GOVERNED WORKSPACE PROTOCOL — ValorizadorXML

- **Mode:** `GOVERNED_PROJECT_WORKSPACE`
- **Central Harness Engine:** `https://github.com/AlvaroAvaca/casa-de-software.git` (branch `main`, local runtime `~/.arnes-factory`)
- **Main Antigravity Dropdown Agent:** `casa-de-software` (`mainAgent: true`, `subagent: true`) backed by 121 internal subagent specialists (`mainAgent: false`, `subagent: true`)
- **MCP Server:** `eiden-harness` (16 tools including `eiden_check_and_auto_update_harness`, `eiden_generate_prebuild_mvp_blueprint`, `eiden_cursor_index_and_graph_audit`, `eiden_cursor_semantic_search`, `eiden_cursor_blast_radius`, `eiden_openclaw_hermes_goal`, `eiden_harness_status`, `eiden_run_closing_review_95pct`, `eiden_run_tenth_man_100pct`, `eiden_dispatch_worker`)

## Mandatory Engineering & Autonomous Routing Invariants
0. **ZERO_HARNESS_IN_PRODUCT_REPOS (Never Commit or Push Harness Files to Product Repositories):**
   - **NEVER commit or push** `.eiden/`, `.agents/`, `.claude/`, `.arnes/`, `.harnesskit/`, `.codex/`, `.cursor/`, `.mcp.json`, `CLAUDE.md`, `eiden_software_factory/`, `Harness-software-house/`, or `HarnesOKIS/` into this product repository. Only product/application code and lightweight pointer files (`GEMINI.md`, `AGENTS.md`, `.gitignore`) belong in product Git repositories.
   - The Harness lives **exclusively** in `https://github.com/AlvaroAvaca/casa-de-software.git` (branch `main`) and is installed/updated on demand on any machine via:
     ```bash
     curl -fsSL https://raw.githubusercontent.com/AlvaroAvaca/casa-de-software/main/install.sh | bash
     # or:
     ~/.arnes-factory/bin/arnes self-update && ~/.arnes-factory/bin/arnes install "$(pwd)"
     ```
1. **Step 0 Autonomous Version Check & Pre-Construction 360° MVP Blueprint Gate (Never Ask Owner to Run CLI Commands):**
   - NEVER ask the Owner (Alvaro) to run CLI commands manually. You (the Agent / `master_work_distributor`) MUST invoke `eiden_check_and_auto_update_harness`, `eiden_generate_prebuild_mvp_blueprint`, `eiden_cursor_index_and_graph_audit`, `eiden_cursor_semantic_search`, and `eiden_cursor_blast_radius` autonomously.
2. **Mandatory Spoken Caller-ID (`[Proyecto + Sesión]`) with Paulina Voice (Non-Blocking):**
   - Every spoken message to Alvaro MUST begin by identifying the **Project Name (`ValorizadorXML`)** and **Session/Agent Name**:
     - `"Desde el proyecto ValorizadorXML, sesión [Agente o Sesión]: Álvaro, ..."`
   - Execute via detached one-shot process (`IsDaemon: false`):
     ```bash
     killall say 2>/dev/null || true; node -e 'const path=require("path"),{spawn}=require("child_process"),p=process.env.EIDEN_PROJECT_NAME||path.basename(process.cwd()),s=process.env.EIDEN_SESSION_ID||process.env.EIDEN_SESSION_NAME||"Casa de Software",m=process.argv[1]||"";const txt=/^(desde el proyecto|habla )/i.test(m)?m:`Desde el proyecto ${p}, sesión ${s}: ${m}`;spawn("say",["-v","Paulina","-r","185",txt],{detached:true,stdio:"ignore"}).unref()' "Desde el proyecto ValorizadorXML, sesión Casa de Software: Álvaro, ..."
     ```
3. **Dual-Language Enforcement:**
   - All internal agent reasoning, subagent prompts, code, comments, and logs MUST be 100% in technical English.
   - All direct communication with the Owner (Alvaro) MUST be 100% in clear Chilean Spanish + Paulina TTS with `[Proyecto + Sesión]` Caller-ID.
