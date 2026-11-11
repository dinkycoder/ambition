# P-25: The platform's name is Agency Lab

Nov 8, 2026 · @dinky

| Field | Value |
| --- | --- |
| Status | Accepted, November 8, 2026 |
| Supersedes | P-16 (keep the Ambition name) |
| Related | [P-23](P-23-aws-platform.md) (AWS), [P-24](P-24-base-chain.md) (Base) and [P-28](P-28-micro-research-and-education-platform.md) (the Micro Research and Education Platform description) |

## Summary

**Ambition becomes Agency Lab, because the platform studies and teaches agency, and the name should say so.** Jaroslav Pantsjoha closes his account of the reason-act-observe loop by observing that each pass lets an agent change course on what actually happened instead of following a fixed script, and that "that feedback is the difference between agency and ambition" (*Building the Agentic Enterprise*, p. 32). Ambition is a plan; agency is a plan that corrects itself against the evidence, which is what the research desk does and what the toolkit lets an agent do safely with money.

## Context

P-16 kept the Ambition name on November 7, 2026, because the mission still fit and keeping the name kept the repository, its history and readers' links intact. Two things changed. The platform now centers on agents acting for the people who own them, which economists call the principal-agent problem, and that is what "agency" names. The book's own vocabulary for safe autonomy is built on the word: Agency Scope matches autonomy to each lifecycle stage (pp. 370–376), and Least Agency gives each agent no more autonomy than its task needs (pp. 351–352).

## Decision

**The name is Agency Lab, never "Agency" alone.** A bare common word is hard to search and hard to own: it already means advertising, staffing and government agencies, and in agent infrastructure AGNTCY, a Linux Foundation project for agent discovery, identity and messaging, reads the same way. "Lab" fixes that and also says what the platform is, a place for research and education.

| Item | Before | After |
| --- | --- | --- |
| Name in prose | Ambition | Agency Lab |
| Document titles and PDFs | "Ambition - …" | "Agency Lab - …" |
| Design tokens and component previews | `"name": "Ambition"` | `"name": "Agency Lab"` |
| Repository | github.com/dinkycoder/ambition and its GitLab mirror | Renamed to `agency-lab` on both, as a separate step the owner takes in each site's settings |
| Mission | "Help AI builders give their agents money safely, one small win at a time." | Unchanged |
| License | MIT, not covering the name | Unchanged, and it doesn't cover the Agency Lab name or any future logo |
| Archived records | Named Ambition | Unchanged, because a dated record keeps the name it had |

**The repository keeps its history.** GitHub redirects the old address to a renamed repository, so readers' links keep working. When the GitLab project is renamed, the mirror workflow's GitLab address must change in the same commit, or the next sync fails.

## Consequences

**Every current document, PDF and design-system file carries the new name, and the decision register gains P-25.** Earlier records in the archive keep "Ambition", so the history reads as it happened.

**The rename costs little now and more later.** The weekly posts are paused, so the public footprint is small, and every document is already being rewritten for P-23 and P-24. This register has now changed the name once and the chain twice in a week, so the name is recorded here to stay fixed.

## Alternatives considered

| Option | Why not |
| --- | --- |
| Keep Ambition (P-16) | Pantsjoha's line makes "ambition" the opposite of what the platform teaches |
| "Agency" alone | Hard to search, hard to own, and easy to confuse with AGNTCY in the same field |

## Revisit when

Only if the mission changes.

## Sources

- Jaroslav Pantsjoha, [*Building the Agentic Enterprise*](https://www.oreilly.com/library/view/building-the-agentic/9781807604455/) (Packt, September 2026), pp. 32, 351–352 and 370–376; the nine-word quotation above is the only book text in this repository
- Linux Foundation, [Linux Foundation welcomes the AGNTCY project](https://www.linuxfoundation.org/press/linux-foundation-welcomes-the-agntcy-project-to-standardize-open-multi-agent-system-infrastructure-and-break-down-ai-agent-silos) (July 29, 2025)
- GitHub Docs, [Renaming a repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/renaming-a-repository), on redirects after a rename
