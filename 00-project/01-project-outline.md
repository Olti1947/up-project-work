---
name: Olt Bajrami
neptun: "P3FEII"
id: "2026-ST-06"
github: https://github.com/Olti1947/up-project-work
---
# Least Privilege on a Budget: an Agent-Native OS for Low-Cost Hardware

Personal AI agents such as OpenClaw are increasingly run on dedicated always-on computers, most often a Mac mini, even though the AI model itself usually runs in the cloud and the local machine is mostly idle. These agents run with their owner's full permissions while constantly reading untrusted content such as emails and web pages, so a single hidden instruction can make them leak data or perform harmful actions. This project designs and builds an agent-native operating system for a low-cost Raspberry Pi, in which the AI agent is treated as an untrusted user: every action it requests is checked against narrow, temporary, task-specific permissions and runs in isolation. The system is managed remotely and used through a chat app. The main goal is a three-way comparison between a Mac mini with macOS, a Raspberry Pi with a standard Linux distribution, and a Raspberry Pi with the agent-native OS, using the same agent and tasks, to separate the effect of cheaper hardware from the effect of the operating-system design on cost, efficiency and security.

## Objectives
- **Primary objective:** Deliver a working agent-native operating system for a low-cost single-board computer, and compare it with a Mac mini and a standard Linux setup in terms of cost, efficiency and security.
- **Target users / stakeholders:** Individuals and small teams running personal AI agents who want them cheap, always on and safe without security expertise; researchers evaluating agent security.
- **Measurable success criteria:**
  - A user can request a task from a chat app and receive the result from the agent-native setup.
  - An action outside a task's permissions is blocked and recorded, while the task's allowed actions still succeed.
  - The same workload and attack set run on all three setups, and cost, power, memory, response time and attack success rate are reported for each.
  - The agent-native setup costs at most €150 in hardware and blocks a substantially larger share of prompt-injection attacks than the standard Linux setup.
- **Constraints:** Low-cost single-board computer (Raspberry Pi 5); built on the Linux kernel, without writing a new kernel; AI models are cloud-hosted; no screen or local login on the device; open-source code and published measurement data; no credentials in the repository.

## Scope
### In scope
- A minimal operating system image for the Raspberry Pi 5 that starts directly into the agent environment.
- Checking every action the agent requests against task-specific, time-limited permissions.
- Running each action in isolation.
- Owner-defined permission limits and user approval of sensitive actions.
- Requesting tasks and receiving results through a chat app.
- Remote management: pairing, permissions, scheduled tasks and an audit log.
- A shared set of realistic agent tasks and prompt-injection attacks.
- A three-way comparison of cost, power, memory, response time and attack containment.

### Out of scope
- Writing a new operating-system kernel.
- Running AI models locally on the board.
- Features that depend on Apple devices, such as iMessage.
- Formal verification and production-grade hardening.
- Commercial distribution and multi-user or multi-tenant deployments.

## Notes
The comparison is the main evaluation method, while the agent-native OS is the main artefact built. The first prototype will support a small set of tools (email, calendar, web browsing on approved sites, and file storage) based on the most common personal-agent tasks. Additional isolation methods, more tools and an optional fourth setup (standard Linux with container-based isolation) will be considered only after the core system and the three-way comparison are reliable. As this is my own project idea, it is pursued together with a TDK entry, subject to course-staff approval.