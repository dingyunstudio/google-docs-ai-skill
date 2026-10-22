# Google Docs AI Editing Skill

[繁體中文](README.md) | [English](README.en.md)

[![Support me on Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/dingyunstudio)

**This Skill provides guidance for AI agents operating on Google Docs.** It is based on methods used in practice by 定沄整合設計工作室 and is intended for AI to read and follow.

This Google Docs editing workflow can be used in ChatGPT chat environments with the required connected tools.

It helps AI edit Google Docs safely: establish the current document state, make changes one structural unit at a time, read back immediately, verify the text and structure, and leave evidence of the actual result.  
This process helps reduce the risk of timeouts or incorrect writes when AI operates directly on Google Docs.

**The Skill provides operating methods and checks. It does not connect to or edit documents itself, and it is not an automatic formatting tool, layout optimizer, or document wizard.** The AI uses connected tools to perform the actual reads and writes. The user confirms the requirements and scope of changes; the AI operates within that approval, reads back, verifies, and reports the results.

This Skill does not guarantee that AI will never make errors or will complete every requested outcome. Results depend on the actual operation and verification performed.

> **Version: 0.1.0.**
>
> The package contains a Skill, eight chapters of operating rules, and two templates. Full native integration testing, independent review of the complete public package, and formal release are still pending.

This English page covers the README. The Skill, references, and templates retain their existing language.

**Quick links:** [Editing scenarios](#capabilities) · [How to use it](#usage) · [Operating chapters](#chapters) · [License and commercial use](#license)

<a id="capabilities"></a>

## How can it help you edit Google Docs?

The following are examples of requests AI can help with by following this Skill, rather than automated features built into the Skill itself. Just say what you want to change in chat. The AI reads the document, agrees on an approach with you, then makes and checks the changes.

### Common editing requests

| What you want to do | What you can say | How the AI helps |
|---|---|---|
| **Change a specific sentence or paragraph** | “Replace the last sentence in paragraph two with the version we just agreed on. Leave everything else alone.” | Changes only that location, then checks the wording, punctuation, and surrounding content. |
| **Change only one occurrence of repeated text** | “That sentence appears twice. Change only the later one and leave the first one alone.” | Finds and changes the later occurrence while preserving the earlier sentence and other content. |
| **Continue after you have updated the document** | “I just updated it. Read it again before you carry on.” | Reads the latest content and re-establishes the edit location so it does not edit from an old draft. |
| **Replace text throughout the document** | “Replace every ‘Draft’ with ‘Final’ in this document. Leave everything else alone.” | Finds every occurrence, makes the replacements, and checks for missed or unintended changes while preserving formatting and link URLs. |
| **Rework the content or layout of the whole document** | “Reformat the whole thing. Keep the wording and the original link.” | Prepares a layout draft, updates the original document after your confirmation, and checks the layout while preserving the wording, links, and tables. |
| **Create a new document as the formal version** | “Tidy up this proposal and make a new document. We'll use the new version from now on.” | Prepares the content and layout, creates the new document after confirmation, and identifies the formal version and its new link. |
| **Replace the original document with a complete new draft** | “This new draft is final. Replace the original content, but keep the original link.” | First confirms an approach and scope that can preserve the original link, proceeds after your confirmation, then checks the complete text, formatting, and link. |

Back up before making changes and check the result afterward. These approaches follow the method used in practice by 定沄整合設計工作室.

### Supported workflows

| What you can say | How the AI helps | What you receive |
|---|---|---|
| “Tidy up this proposal and turn it into a new Google Doc.” | Prepares the full content and layout, creates the new document after your confirmation, then checks the online result. | A new Google Docs link with the prepared content and layout. |
| “Change the later ‘The weekly content is awaiting confirmation’ to ‘The weekly content has been confirmed.’ Leave everything else alone.” | Finds and changes only the specified sentence, then immediately checks that the surrounding content is preserved. | The specified sentence updated in the original document, with other content unchanged. |
| “Reformat this whole document. Keep the wording and the original link.” | Prepares a layout draft, updates the original document in steps after your confirmation, checks each change, and finishes by checking the complete text, links, and tables. | The same document link with the revised layout. |
| “The next paragraph disappeared after that edit. Help me work out how to recover it.” | Identifies the affected content, compares it with the original or a backup, and proposes a recovery plan before proceeding with your confirmation. | An explanation of the affected content, how it can be recovered, and the actual outcome after the recovery is approved and performed. |

Keeping the original link, creating a new file, or changing the formal version follows the plan you confirm. The same applies to sharing settings.

<a id="usage"></a>

## How to use it

### Requirements (ChatGPT Chat)

- **ChatGPT Plus**: the baseline plan for this project's ChatGPT Chat workflow. Available capabilities still depend on the account and connected tools.
- **Connected Google Drive/Docs tools and document editing permission**: required to read, edit, and read back the document.
- **A connected GitHub tool and repository read access**: required when loading this Skill from GitHub. For a private repository, confirm that the connected account has access.

### Initial load

Ask the AI to read this package from GitHub, or provide this folder in an environment that supports local Skills, starting with [SKILL.md](SKILL.md).

```text
@GitHub Please read dingyunstudio/google-docs-ai-skill.
Use it to help me edit this Google Doc: [link]
Read the content first. I'd like to make the layout clearer and easier to read.
```

### Continue in the same conversation with DYS

After loading it in the same conversation, you can use “DYS” to refer to this Skill:

```text
Use DYS for this document: [link]
Keep the wording unchanged; just improve the layout.
```

You can follow up with requests such as “Change only the later occurrence of that sentence” or “Replace every occurrence of ‘Draft’ with ‘Final’.” The AI carries forward the confirmed document and constraints. A different document, tab, or scope still requires confirming the target. In a new conversation, make the Skill available again rather than relying on it having been loaded in the previous conversation.

### How the AI handles your request

1. **Provide the document link and what you want to do.** Constraints already established in the conversation carry forward.
2. **The AI reads the relevant Skill chapters and the current document**, establishes its identity, tabs, structure, and edit boundaries, and records a [task contract](templates/task-contract.md). This is the AI's working record, not a form for you to fill out. It obtains technical details such as tab IDs, revisions, indices, and risk or verification levels from available tools. It asks only about ambiguities that materially affect the goal, scope, or tradeoffs.
3. **The AI presents a concrete change and verification plan in plain language** and proceeds within your explicit approval of that plan, following the original SOP rules. A request to improve visual layout starts with preserving the wording; it does not automatically authorize rewriting the content.
4. **After each write unit, the AI immediately reads back and verifies the result.** The final [verification report](templates/verification-report.md) describes actual changes, protected content, evidence, and anything not verified. Conversational requests retain the SOP's required reporting, approval, and stopping conditions.

### Environment and local installation

Actual edits require suitable native Google Docs tools. Access to GitHub alone does not provide Docs write access, local document production, or visual inspection capabilities.

If only plain-text reading is available, the AI can study the content or propose changes. Verifying paragraphs, headings, styles, lists, tables, or links requires the corresponding structural data. If writing or visual inspection is unavailable, the AI states what it can deliver and does not claim to have edited the document or passed layout checks.

Local Skill installation depends on the AI tool. Keep the folder's references, templates, LICENSE, and LICENSES together so relative paths and license terms remain available.

<a id="chapters"></a>

## Chapters and source principles

### Operating chapters

| File | Original section numbers / purpose |
|---|---|
| [00 Overview](references/00-overview.md) | Workflow, rule index, and navigation by need |
| [01 Governance and task control](references/01-governance-and-task-control.md) | §00–03: identity, authorization, current evidence, required reports |
| [02 Preparation and trust baseline](references/02-preparation-and-trust-baseline.md) | §04–06: CSV, backup, revision, risk, and verification depth |
| [03 Boundary and structural planning](references/03-boundary-and-structural-planning.md) | §07: boundaries, structural units, and the two correction models |
| [04 Execution and verification](references/04-execution-and-verification.md) | §08: per-unit writes, readback, integrity, evidence |
| [05 Stop and safeguards](references/05-stop-escalation-and-guards.md) | §09–10: stopping, recovery sources, connector guards |
| [06 Modes and checklists](references/06-operating-modes-and-checklists.md) | §12–14: Modes A/B/C, failure patterns, checklists |
| [07 Maintenance and responsibilities](references/07-maintenance-and-cross-sop.md) | §15–16: rule reuse, read-only review, input responsibilities |

### The original method and this public edition

File prefixes are package chapter numbers, distinct from the original section numbers retained in the text. The original rule IDs, L0–L5/V1–V5 levels, conditions, exceptions, and Stop/Recovery boundaries are preserved. Public adaptations remove private identifiers and history, replace private cross-manual references with task and evidence inputs, and point the known Recovery Escalation navigation reference to §09.3.

This public edition is adapted from 定沄整合設計工作室's SOP01. It does not introduce a new operating method.

<a id="license"></a>

## License and commercial use

### Noncommercial use

© 2026 定沄整合設計工作室. Documentation and prose templates are licensed under [CC BY-NC-SA 4.0](LICENSES/CC-BY-NC-SA-4.0.txt). See [LICENSE](LICENSE) for file coverage.

### Commercial permission and contact

This project is source-available and free for noncommercial use under its license; it is not licensed as OSI-defined open source. For commercial permission, see [COMMERCIAL.md](COMMERCIAL.md) and contact [dingyun.studio@gmail.com](mailto:dingyun.studio@gmail.com).

Questions and improvement suggestions are welcome. Licensing and commercial sublicensing arrangements must be clarified before incorporating substantive third-party contributions.

## ☕ Support this project

If this Skill helps you, consider [buying me a coffee](https://ko-fi.com/dingyunstudio) to support ongoing maintenance.

Support is voluntary and does not include commercial permission. For commercial use, see [COMMERCIAL.md](COMMERCIAL.md) and contact the studio separately.
