# From Approval Loops to Autonomous Agents with Docker

A 90-minute hands-on workshop that walks through the Docker primitives behind safe AI agent autonomy. It builds a working mental model for the trade-offs you make when you hand an AI agent meaningful capability on your machine, then puts the corresponding safety primitives in place one at a time.

## The premise

Modern AI agents are useful because they take real actions on your machine: they read files, run commands, hit the web, build containers, write code. That capability is also where the risk lives. Give an agent unrestricted access and a single bad prompt can do real damage. Give it too little and it's useless. The middle path is **scoped autonomy** — the agent gets exactly what it needs for the work, and nothing more.

Docker has built a stack of primitives that make scoped autonomy practical. This workshop goes through them one safety box at a time.

## What the workshop covers

The core arc is six hands-on steps, each tightening one part of the agent's environment:

- **Step 1: What the agent is.** Create a sandbox and connect to it. The agent reports back on its environment, the kernel it has access to, the user it runs as, and the directory it can see.
- **Step 2: How the boundary holds.** Prove the isolation with hands-on tests from inside and outside the sandbox. The workspace shares both directions; host files outside it are unreachable; secrets stored on the host stay on the host.
- **Step 3: What it can reach.** Govern the sandbox's outbound network with a declarative policy. Default deny, with allow rules you write explicitly. The audit log shows every request the proxy enforced.
- **Step 4: What tools it has.** Attach an MCP (Model Context Protocol) server to give the agent a specific capability. We register a Wikipedia MCP server and watch the agent reach Wikipedia content through the tool layer rather than through direct network access.
- **Step 5: What it ships.** Have the agent build a real container, scan it for vulnerabilities with Docker Scout, then swap the base image to a Docker Hardened Image (DHI) and rescan. Same code, dramatically lower CVE count.
- **Step 6: How to share the setup.** Package the entire configuration as an sbx kit. One directory, committable to git, re-runnable by anyone on your team with a single sbx command.

Two add-on modules step outside the sbx story to show **Docker Agent**, a different layer of Docker's agent platform aimed at multi-agent orchestration:

- **Step 7: Multi-agent orchestration.** Write a six-role research team in a Docker Agent yaml. Two researchers (one on Wikipedia, one on the academic literature), an analyst running on a heavier model for synthesis, a writer, and a publisher that renders the final report as a styled academic-paper-formatted HTML page.
- **Step 8: Per-role tool isolation.** Probe each role's `toolsets` list to see that the runtime boundary holds, not just as a yaml convention. The boundary is observable in the trace: each role only ever invokes the tools its yaml grants.

## Lessons you'll walk away with

- **Capability isolation belongs at the runtime, not in the prompt.** When a role can't do something, the trace shows it never tried — there's no tool call to make. Prompts are guidance; toolsets are the contract.
- **Composable primitives beat monolithic guardrails.** Each Docker primitive (sandbox isolation, network policy, MCP, DHI, sbx kit, Docker Agent) addresses one slice of the agent's surface area. You compose only what the task needs.
- **Reproducible setups scale.** A kit committed to git turns a personal sandbox configuration into something a team can stand up reliably with one command.
- **Multi-agent and single-agent are different shapes.** sbx scopes one agent's environment; Docker Agent scopes each role within a team. They're complementary layers, not strictly stacked — pick the one that matches the shape of the work, or compose both when the architecture justifies it.

**[Open the workshop](https://dockterdan.github.io/ai-engineer-workshop/)**
