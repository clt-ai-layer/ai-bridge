# 🌉 AI Bridge

**A growing collection of reusable prompts that make AI-assisted development more reliable, efficient, and structured.**

AI coding assistants are powerful — but raw. Without structure, they lose context, repeat mistakes, and waste tokens. AI Bridge is an open collection of battle-tested prompts that solve real workflow problems when working with LLMs on complex codebases.

Each prompt is **tool-agnostic** — use them with Cursor, Copilot, Claude, ChatGPT, Gemini, or any LLM-based assistant.

---

## 📦 Prompts

| Prompt | Category | Description |
|--------|----------|-------------|
| [`create_handoff.md`](./Prompts/Handoff/create_handoff.md) | Session Management | Generate a structured handoff document before ending a session |
| [`resume_handoff.md`](./Prompts/Handoff/resume_handoff.md) | Session Management | Resume work from a handoff document in a fresh session |

> More prompts coming soon. Contributions welcome!

---

## 🤝 The Handoff Protocol

### The Problem

Every AI coding assistant has a finite context window. Push past it and you enter the **Dumb Zone** — the model starts looping, hallucinating, or quietly undoing its own work.

The instinctive reaction? Copy-paste whatever feels relevant into a new chat and hope for the best. But that's lossy, messy, and error-prone. You lose decision history, the new session re-discovers problems already solved, and you waste tokens re-explaining context.

### The Solution

The Handoff Protocol turns session transitions from a liability into a feature. Two prompts form a relay race: one agent writes the baton, the next picks it up — with zero context loss.

#### 1. Create a Handoff

When you sense a session is losing sharpness — or a logical milestone is reached — tell your AI to use the `create_handoff` prompt.

The AI produces a structured `.md` file containing:
- **Tasks** — what's done, in progress, and planned
- **Recent changes** — exact files and lines modified
- **Learnings** — patterns discovered, bugs root-caused, pitfalls to avoid
- **Artifacts** — every document produced or updated
- **Next steps** — a clear action plan for the successor

#### 2. Resume from a Handoff

Open a fresh session (100% of its attention budget), and tell it to use the `resume_handoff` prompt with the path to your handoff file.

The new AI will:
1. Read the handoff document and all referenced files
2. Verify the current state against the handoff
3. Present a structured analysis with recommended next actions
4. Wait for your approval before proceeding

#### 3. Steer, Don't Autopilot

> ⚠️ Always read the handoff yourself and adjust direction if needed. The AI often needs your expertise and knowledge of the end goal to chart the best course of action.

### The 5 Rules for Avoiding the Dumb Zone

The handoff prompts implement rule #4, but here's the full playbook:

1. **The 60% Rule** — Switch sessions before the AI's memory saturates.
2. **Separate thinking from doing** — One chat for research, one for planning, one for code.
3. **Cut loops short** — If the AI proposes the same mistake 3 times, the context is polluted. Leave.
4. **The Handoff Protocol** — Summarize state before switching sessions. ← *You are here*
5. **One chat, one task** — Break complex work into focused sessions.

---

## 🚀 Quick Start

1. **Copy** the prompts you need into your project or AI tool's prompt/rules directory.
2. **Adapt** the file path conventions to match your project structure.
3. **Use them** as system prompts, slash commands, or manual instructions.

## 🔧 Usage with Different Tools

| Tool | How to use |
|------|-----------|
| **Cursor** | Add as project rules in `.cursor/rules/` |
| **GitHub Copilot** | Add to `.github/copilot-instructions.md` or use as chat context |
| **Claude / ChatGPT** | Paste as system prompt or first message or Make it a skill |
| **Gemini CLI / Antigravity** | Add as agent rules in `.agent/rules/` |
| **Any LLM** | Include in the system prompt or conversation start |

## 🤝 Contributing

Have a better template? A prompt for a different phase of the AI workflow? Open a PR or issue — this repo is meant to grow.

## License

MIT — use it, fork it, adapt it.
