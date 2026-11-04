# Ambition Roadmap and Decision Register

Nov 3, 2026 · @dinky

## Summary

**Ambition keeps its published 12-week plan and its January 26, 2027 demo; the book's MREP case study now governs how Ambition is built and where it grows.** *Building the Agentic Enterprise* follows one fictional firm, ACME Research, as its Macro Research & Education Platform (MREP) grows from one agent into a governed multi-agent platform.

Nine of the book's thirteen chapters land inside weeks 1 to 12 as engineering discipline. They add a Decision Register, a check anyone can run for each week, control kept outside the model, an audit trail and an evaluation gate, without moving any published date.

The other four chapters describe what comes after the demo: a DeFi research and education desk. Its agents use Ambition's own wallets, limits and statements to buy data, write cited safety briefs and beginner lessons, and later sell those briefs to other agents. The desk is a candidate for the ladder's fifth rung, so it starts only if the week-12 evidence chooses it and the verified-owner gate has passed, planned for May 2027.

The mission stays the same, because a research desk that gives its own agents money safely is the mission in practice.

## Roadmap at a glance

![Nine chapters ride the published ladder; four more build the desk at rung 5](img/agentic-enterprise-roadmap.png)

Rungs 1 to 3 are the published 12 weeks, unchanged; the book's chapters only add checks to them. Rung 5 becomes the desk only if week 12 chooses it.

## Weeks 1 to 12: the book as the operating discipline

**Nine chapters change how the published weeks are built, not what they build or when.** Each row names the week it lands in and a check anyone can run, so the demo proves a working system rather than a prototype that only runs on one laptop.

| Book chapter | Lands in | What it adds to the published week | Done when |
| --- | --- | --- | --- |
| 1. Why agentic systems fail | Weeks 1–2 (Nov 2–14) | Opens this Decision Register and runs each module through the book's Trinity of Value test before it is built, which guards against the PoC Trap (a demo that never reaches real use) | The register is in the repo, and weeks 3 to 12 each have a one-line Done-When check |
| 2. The agentic AI foundation | Weeks 1–6 (Nov 2–Dec 12) | The wallet agent runs a reason-act-observe loop: it decides, calls one tool (read a balance, pay, call the x402 service), then checks the result before its next step | In week 6 the agent buys from the x402 service unaided, and every tool call is logged with its inputs and result |
| 7. Security, identity and guardrails | Weeks 7–8 (Dec 14–26) | The week-8 security checklist maps each risk in the OWASP Top 10 for Agentic Applications to an Ambition control | Each of the ten risks has a named control or an accepted-risk entry in the register |
| 3. Single-agent and multi-agent systems | Week 9 (Dec 28–Jan 2) | Agent version 1 stays one agent, and the register records the measurable trigger that would justify a second | Register entry D-06 names the trigger |
| 4. Core architectural patterns | Weeks 9–11 (Dec 28–Jan 16) | Control is split from execution: the model proposes a payment, code checks it against the limit and allow-list, and only then does a tool pay. A reconciliation step after each payment is the book's reflection pattern | A test proves a fooled prompt cannot reach a payment without passing the code check |
| 8. Building and deploying agentic workflows | Weeks 9–12 (Dec 28–Jan 23) | Each module ships with its Done-When written as a test, and every run writes a structured log (run ID, tool calls, tokens, test money spent) and stops at its budgets | The week-9 audit post is generated from these logs |
| 9. State, memory and decision persistence | Weeks 10–11 (Jan 4–16) | Statements become the decision audit trail, and escrow plus approval above the limit become the human approval gates | Any payment traces from its statement line to its request, evidence, version, approver and transaction hash |
| 10. AgentOps and EvalOps | Weeks 11–12 (Jan 11–23) | Alerts plus permission revocation form the kill switch, and a GitHub Actions evaluation gate blocks any merge that fails a catastrophic test | The evaluation suite runs on every pull request, and catastrophic tests pass 100% |
| 13. The reference architecture | Week 12 (Jan 18–23) | The capstone write-up includes Ambition's reference architecture and this register, the package a reviewer asks for before backing more work | The January 26 demo shows the architecture and the register |

Rows run in the order the weeks do, so chapter 7 comes before chapter 3. The safety rules from *Building AI Agents for Finance* already in the [reading notes](research/building-ai-agents-for-finance-notes.md) carry on unchanged.

## After the demo: the research and education desk

**If week 12 chooses it, the desk becomes rung 5 and runs from May 3 to November 13, 2027, one chapter at a time.** It starts after the verified-owner gate, because the ladder lets each rung pass its gate before the next begins, and a missed gate moves these dates rather than lowering the bar.

The desk is Ambition's first serious user. Its agents get money only through Ambition's wallet, limit, escrow and statements, so every week of research also tests the toolkit under real load.

| Book chapter | Lands in | What Ambition builds | Done when (starting targets) |
| --- | --- | --- | --- |
| 5. Multi-agent orchestration | Desk 1 (May 3–Jun 12) | One research agent buys public data over x402 and writes a weekly DeFi safety brief and a beginner lesson. An analyst, an educator and an editor that supervises the others join one at a time, each only after evaluation shows a gain | Four weekly briefs in a row, every claim cited and every run under budget |
| 6. Context, memory and knowledge | Desk 2 (Jun 14–Jul 24) | The context moat: a cited library of protocol docs, contract audits, exploit post-mortems and public sanctions lists, which name crypto wallet addresses, searched by meaning and by keyword | A 50-question test set answered with sources, and "insufficient evidence" returned whenever the library lacks the answer |
| 11. Platform engineering | Desk 3 (Jul 26–Sep 4) | A paved road: a template that gives any reader's agent a wallet, limit, statements, logs and evaluations by default, plus a guide for adding a new desk agent | One reader, not the maintainer, ships an agent from the template that passes the evaluation suite |
| 12. Operating models and business transformation | Desk 4 (Sep 6–Oct 16) | Service-as-Software: other builders' agents pay per brief over x402 on the test network, which is business-to-agent commerce. Each workflow gets a RACI saying who is responsible, accountable, consulted and informed | Ten outside agents have paid for a brief, every workflow has a RACI, and an evidence review decides whether to form the company |
| 13. The reference architecture, final | Oct 18–Nov 13 | The architecture and register updated for the final capstone submission | Submitted ahead of the December 2027 graduation; the capstone due date is still an open question |

**The desk researches risk and safety, never prices.** It explains what could go wrong in a protocol or a counterparty and teaches beginners how to check, but it makes no price calls, trade signals or personal recommendations. That keeps it on the research-and-education side of the line, keeps the plan's rule that nothing here is financial advice, and plays to Ambition's mission.

## The week-12 decision gets a fifth row

**The desk competes on evidence like every other path, so it enters the plan as one more row of the week-12 table.** The row is proposed (D-02) and goes into the [build-in-public plan](build-in-public-plan.md) only once you accept it.

| If at week 12… | Then |
| --- | --- |
| Readers keep completing the lesson challenges and builders pay the x402 service from their own code | Choose the research and education desk as rung 5, because it serves both signals at once: people who want to learn and builders who will pay agents for data |

## How the books are used

**Ambition adopts the book's patterns without its platform.** The reference build in *Building the Agentic Enterprise* runs on Google Cloud, with Google's Agent Development Kit (ADK), Gemini models and Cloud Run, and the author teaches the disciplines so they carry over to other stacks. Ambition stays on Python, Base Sepolia and GitHub Actions, and any agent framework is chosen by scoring candidates on the nine dimensions in chapter 3 of *Building AI Agents for Finance* (D-08).

**Neither book goes into Git.** This roadmap summarizes *Building the Agentic Enterprise* in its own words and cites it by chapter, the same rule the reading notes set for the other book. Named ideas such as the PoC Trap, the Trinity of Value and the MREP Decision Register belong to the book and are credited to it.

## Starter Decision Register

**Sixteen decisions start the register: six already made in the plan and reading notes, nine proposed here and one left open.** It is Ambition's version of the MREP Decision Register from chapter 13, the record of every decision the design rests on. Update a status as each decision moves, and add each new decision as a row with the next ID.

| ID | Decision | Status | Why | Revisit when | Chapter |
| --- | --- | --- | --- | --- | --- |
| D-01 | The 12-week plan, its ladder and the January 26 demo stay as published; the book shapes how they are built | Proposed | Readers already follow week 1, and a missed gate moves a date, never the bar | Not before the demo | 1 |
| D-02 | The research and education desk is a week-12 option for rung 5, not a commitment | Proposed | Evidence, not enthusiasm, chooses rung 5 | Week 12 (Jan 18–23) | 1, 12 |
| D-03 | Agents spend only test money on Base Sepolia and never touch a real-money account | Accepted | Payments are final, and beginners copy what the build does | After an independent contract audit | 7 |
| D-04 | The desk reads real-network data but spends only on the test network | Proposed | DeFi research needs real protocols' data, and reading moves no money | Desk 1 start | 6 |
| D-05 | The desk covers risk, safety and lessons, with no price calls, trade signals or personal recommendations | Proposed | It stays research and education, matches the mission and keeps "not financial advice" true | Before any paid offer to people | 12 |
| D-06 | One agent with tools carries weeks 1 to 12; a second joins only when evaluation shows a measurable gain | Accepted | More agents add cost and failure modes before they add value | When the evaluation suite shows one agent missing its Done-When because its context is too full | 3 |
| D-07 | Control lives outside the model: the limit in the contract, the allow-list in the tool layer, approval above the limit | Accepted | A fooled model still cannot overspend | Only ever tightened | 4, 7 |
| D-08 | Adopt the book's patterns, not Google Cloud, and pick any framework by a scored comparison | Open | Ambition already runs on Python, Base Sepolia and GitHub Actions, and the patterns carry over | Before Desk 1 | 2, 8 |
| D-09 | Every claim in a brief or lesson carries a source, and "insufficient evidence" is a valid answer | Proposed | Readers can check the work, and a cited "don't know" beats a confident guess | Desk 2 test set | 6 |
| D-10 | Statements are the decision audit trail: one record per payment binds request, evidence, version, guardrail decisions, approver and transaction hash | Accepted | Anyone can trace why money moved | Week 10 | 9 |
| D-11 | Catastrophic failures (overspending, a wrong recipient, a leaked key) must pass 100% in a CI evaluation gate | Proposed | The reading notes already demand 100% on these, and CI makes the check automatic | Week 11 | 10 |
| D-12 | The kill switch is revoking the agent's spending permission plus a repository flag that stops scheduled runs | Proposed | One action stops the spending and the other stops the work, and both take seconds | Week 11 | 10 |
| D-13 | Each release pins model IDs and hashes prompts, so a prompt change is a code change | Accepted | Any result traces to the exact version that produced it | Every release | 8, 10 |
| D-14 | The week-8 checklist maps every OWASP agentic risk to a control or an accepted risk | Proposed | A standard list makes the security review harder to skip than a homemade one | Week 8 | 7 |
| D-15 | Book PDFs stay out of Git; docs summarize them in their own words and cite chapters or pages | Accepted | The repo is public and mirrored, and both books' copyright forbids storing them | Never | — |
| D-16 | Briefs are sold to other agents over x402 on the test network before any real-money pricing | Proposed | It proves business-to-agent demand at no risk | Desk 4 | 12 |

## Plain-language terms

**Every term this roadmap adds is defined here, in the same plain style as the design guidelines' glossary.**

| Term | Plain meaning |
| --- | --- |
| Audit trail | A record that shows what an agent did, why, with which version and who approved it, so anyone can check it later |
| Base Sepolia | Coinbase's free practice blockchain, where all of Ambition's money is test money |
| Business-to-agent commerce | Selling to other companies' AI agents rather than to people, here by charging per request over x402 |
| Context moat | Knowledge a competitor can't easily copy, fed to the agents so their answers beat a general model's |
| Contract audit | An expert review of a smart contract's code that looks for ways money could be lost |
| Counterparty | Whoever is on the other side of a payment or deal, such as the wallet an agent pays |
| DeFi | Decentralized finance: lending, trading and payments run by smart contracts instead of a bank |
| Decision Register | One table of every decision the design rests on, with its reason and when to revisit it |
| Done-When | A check anyone can run that says a piece of work is finished, written before the work starts |
| Evaluation gate | An automatic test run that blocks a change from merging if the agent fails a critical test |
| Exploit post-mortem | A write-up of how a protocol lost money to an attack and what fixed it |
| Kill switch | A fast way to stop an agent: here, cancelling its spending permission and pausing its scheduled runs |
| Orchestration | One supervising agent hands tasks to helper agents and checks their work |
| PoC Trap | The book's name for a proof of concept that impresses in a demo but never reaches real use |
| Protocol | A DeFi service built from smart contracts, such as a lending market |
| RACI | A chart naming who is Responsible, Accountable, Consulted and Informed for each task |
| Reason-act-observe loop | How an agent works: it decides what to do, uses one tool, looks at the result, then decides again |
| Sanctions list | A government list of people, companies and, in the US, crypto wallet addresses that may not be paid |
| Service-as-Software | The book's term for selling the finished work an agent does, rather than the software that does it |
| x402 | Coinbase's standard for agents paying for things on the web, one request at a time |

## Sources

- Jaroslav Pantsjoha, [*Building the Agentic Enterprise*](https://www.oreilly.com/library/view/building-the-agentic/9781807604455/) (Packt, September 2026), the MREP case study and the chapter structure mapped here
- Hanane Dupouy and Fayssal El Mofatiche, [*Building AI Agents for Finance*](https://reference-global.com/book/9781837022281) (Packt, 2026), with Ambition's adopted rules in the [reading notes](research/building-ai-agents-for-finance-notes.md)
- OWASP GenAI Security Project, [OWASP Top 10 for Agentic Applications for 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications/) (December 9, 2025)
- US Treasury, [OFAC FAQ 563](https://ofac.treasury.gov/faqs/563), on how the sanctions list records digital currency addresses
- Ambition, [Build in Public: Mission and 12-Week Plan](build-in-public-plan.md), the weeks, ladder, gates and week-12 decision this roadmap keeps
