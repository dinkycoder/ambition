# Usability Testing for Ambition: Research and Plan

Nov 4, 2026 · Dayn Kirksey

## Executive summary

You can run credible usability studies of Ambition for $0 to $100 by combining free tools, and Figma Make lets you test Ambition's money flows about six modules earlier than planned. Free tiers cap each study at 3 to 15 responses. That is enough, because Nielsen Norman Group found that five users per round catch about 85% of usability problems.

For Ambition, the core method stays free: moderated think-aloud sessions with five developers per round, recruited from your LinkedIn audience. Figma Make turns a typed prompt into a clickable prototype with working buttons and forms. Testers can therefore complete a "Send 5 test USDC" task with simulated money and no wallet at all.

That shift lets unmoderated tests in UXtweak Free and Lyssna Free cover the spend-confirmation dialog in modules 4 to 5, before the zkLogin build exists. Free session replay from PostHog or Microsoft Clarity then covers the live testnet app from module 7.

## Tools compared

UXtweak, Lyssna, Figma and PostHog cover almost everything you need for free; the paid panels add little for a crypto developer tool. Prices were checked on November 2, 2026 unless the cell says otherwise.

| Tool | Free tier | Cheapest paid | Panel cost | Discounts | Fit for Ambition |
| --- | --- | --- | --- | --- | --- |
| [UXtweak](https://www.uxtweak.com/pricing/) | 15 responses a month with per-tool caps, 1 active study, 1 seat, unmoderated only, results viewable for 14 days | Business, about €92 a month billed annually (third-party listings) | Business plan only; vendor says from $10 per participant | Extra discount for students and schools on request | High for card sorts, tree tests and first-click tests |
| [Figma](https://www.figma.com/resource-library/ai-usability-testing/) | Your Education plan: prototype links testers open without an account; FigJam boards | Not listed on the page | None; Make connects to Maze, Helio and Zigpoll | Education plan | High: Make prototypes with simulated test money remove the wallet barrier |
| [Lyssna](https://help.lyssna.com/en/articles/4953377-plan-and-pricing-overview) | 3 seats, unlimited quick studies, 15 viewable self-recruited responses per test | Growth $199 a month, or $165 billed annually | About $1 per participant-minute | Not confirmed | High for 5-second, first-click and preference tests |
| Maze | 5 seats, 1 study a month (third-party read, Oct 12, 2026) | $99 Starter reportedly hidden in the US; Enterprise custom | Credits about $5 each | Student offer unverified | Medium: strong Figma link, but 1 study a month |
| [Useberry](https://www.g2.com/products/useberry/pricing) | 10 responses a month, 1 project, 1 seat | Growth $79 a month, or $67 billed annually | Panel available; price not confirmed | 50% off Growth for students (G2) | Medium-high for Figma prototype flows |
| Lookback | No free plan; trial only | Freelance $299 a year for 10 sessions | $49 per extra panel tester | Not confirmed | Medium for moderated sessions |
| [PostHog](https://volument.com/blog/posthog-pricing-2026-plans-costs-and-how-billing-really-work/) | 1M events, 5,000 recordings, survey responses reported as 1,500 or 250 a month | Pay as you go | None | Not confirmed | High: replay, surveys and SUS on the live app |
| [Microsoft Clarity](https://www.clarity-insights.com/blog/what-is-microsoft-clarity.html) | Free; up to 100,000 sessions a day, recordings kept 30 days | None | None | None | High for the live testnet app |
| [User Interviews](https://www.userinterviews.com/pricing) / [Prolific](https://researcher-help.prolific.com/en/articles/445239-what-is-your-pricing) | None | User Interviews $49 B2C or $98 B2B per session; Prolific rewards plus a 42.857% fee | Incentives extra; Prolific minimum $8 an hour | Prolific academic rate 33.3% | Low: few crypto developers |
| UserTesting | None | About $149 a session, 10-session minimum (competitor blog) | Included | None found | Benchmark only |

Where a cell has no link, the figure comes from third-party comparisons such as [Koji](https://www.koji.so/blog/lyssna-pricing-2026), [User Insight](https://userinsight.ai/blog/maze-pricing), [Listen Labs](https://listenlabs.com/articles/best-usertesting-alternatives/) and [UXtweak's blog](https://blog.uxtweak.com/userlytics-vs-usertesting/), which compete with the tools they price.

# Part 1: The research

## 1. UXtweak in depth

**The free plan is real for card sorts and tree tests, and a three-person pilot for everything else.** UXtweak's [pricing page](https://www.uxtweak.com/pricing/) (modified October 17, 2026) gives Free 1 seat, 1 active study at a time and 15 responses a month, unmoderated only. Card sorts get 10 responses and 20 cards, tree tests 10 responses and 2 tasks, and surveys 10 responses. Prototype, website, first-click, 5-second, preference and mobile tests get 3 responses and 1 task each.

Results stay viewable for 14 days unless you upgrade, although data is stored for 12 months. Live interviews, the participant panel, AI transcripts, exports and consent-form customization are all paid. I could not confirm whether Free includes screen and voice recordings, because those checkmarks did not render.

**The cheapest paid plan is Business, at about €92 a month billed annually** according to third-party listings such as [Crozdesk](https://crozdesk.com/software/uxtweak/pricing); the vendor page's price did not render. UXtweak's own table now lists 350 responses a month, moderated live interviews, 20 AI credits, exports and panel access in 8 countries. Older listings said 50 responses, so confirm the allowance at checkout.

**Ask for the student discount first, because it may make Business free.** The pricing FAQ says students and schools "qualify for an extra discount" by email. Several [G2](https://www.g2.com/products/uxtweak/reviews) and [Capterra](https://www.capterra.com/p/193026/UXtweak/) reviewers report free educational access for a master's thesis or classes.

**The panel is paid and doesn't target crypto developers.** Buying panel participants needs Business, and UXtweak's own blog says they [start at $10](https://www.uxtweak.com/user-participant-recruitment/). I found no "Web3 developer" filter among its targeting attributes. Bringing your own participants by link costs nothing.

**Wallet extensions are its weak spot.** Website tests need a JavaScript snippet on your site or UXtweak's [Chrome extension](https://chromewebstore.google.com/detail/uxtweak/dagniddgipkffcehffkjgbdobhldacgl?hl=en), which is desktop only ([setup guide](https://www.uxtweak.com/help/website-testing-setup/launching-a-website-testing-study/)). Remote testers can't reach a localhost build, so Ambition needs a public preview URL. Testers would also need a funded wallet on Sui's test network, which is why the Figma Make prototype (section 2) and zkLogin sign-in with sponsored transactions (section 5) matter.

**Its privacy claims are strong but self-reported.** UXtweak says it stores all data in the EU, complies with [GDPR](https://www.uxtweak.com/legal/gdpr-compliance), keeps AI opt-in and "never train\[s\] our models on your data" ([privacy by design](https://www.uxtweak.com/legal/privacy-by-design/)). On Free, an NDA can only be a required "I agree" screening question linking to a PDF, which is weaker than a signature.

**Reviews praise breadth and support and criticize limits.** G2 lists about 47 reviews averaging 4.7 out of 5. Common complaints are the learning curve, no concurrent tests on Free, and a response cap that ["runs out fast"](https://makerstack.co/reviews/uxtweak-review/).

## 2. Figma's AI usability-testing workflow

**Figma's [AI usability testing guide](https://www.figma.com/resource-library/ai-usability-testing/) adds the one capability that changes the plan: clickable prototypes that need no wallet and no Figma account.** The page is undated and lists no prices, so treat its tool claims as Figma's framing rather than verified findings. It cites Figma's 2025 AI report, which found that 24% of designers and 40% of developers already use AI during testing.

**Figma's workflow has three steps, and each one maps onto your plan.**

1. **Prototype.** Build interactive prototypes before development so several directions can be tested at once. Figma Make generates clickable prototypes from prompts, with buttons, links and forms already connected, and testers open a view-only link without a Figma account.
2. **Predict.** Run AI audits of accessibility (contrast, text size, screen readers), visual hierarchy (5-second, first-click and heatmap-style checks) and logic gaps (dead-end links, missing error states). Human sessions can then focus on the problems that need judgment.
3. **Analyze.** AI summarizes each session and flags confusion, drop-offs and unexpected behavior. Figma advises asking for findings screen by screen, then going back to Figma to iterate.

**Figma Make is the change, because a working prototype can hold simulated test money.** A tester confirms a payment, the balance drops, the spend meter fills and the transaction status turns Final, with no wallet involved. Built from Ambition's tokens and money components, the prototype tests the same dialog that will ship.

Two things are unverified. I don't know whether your Education plan includes Figma Make or how many AI credits it allows. I also don't know whether a Make prototype can carry UXtweak's snippet, although UXtweak's Chrome extension works on any site on desktop.

**FigJam and Dev Mode fill the gaps around a session.** Figma recommends FigJam for mapping personas and research questions before you build, and for observers to watch sessions live and brainstorm. Dev Mode then confirms the build matches the tested design, which your design guidelines already require.

**The Predict step is already half-built.** Your design guidelines run contrast tests and Carbon's code audit on every change. The plan makes that pass, plus a check for dead ends and missing error states, the gate before each human round.

**Synthetic users and AI heatmaps are a first pass at most, by Figma's own account.** The page names Behavr, which simulates AI users for heatmaps and flow analysis, and Attention Insight, whose claim of "up to 96% accuracy" against eye-tracking is the vendor's own. Figma says AI is "not so good at nuance" and can't replace people, because it lacks real habits and context, so synthetic tests should be followed by a small study with real participants.

For Ambition, that makes synthetic users optional and structural only.

**Check Figma's privacy settings once.** Figma says you can opt out of having your data train its AI in account settings, and that anonymization varies by platform. A Make prompt sends its words to an AI model, which is acceptable for Ambition's public work.

The page also lists Maze, UserTesting, Lyssna, Hotjar, Useberry, Lookback and UserZoom, which section 3 covers, plus Helio and Zigpoll as Make integrations for analytics, recordings and heatmaps.

## 3. Alternatives

**Lyssna has the most generous free plan for quick design tests.** Its [help center](https://help.lyssna.com/en/articles/4953377-plan-and-pricing-overview) lists 3 seats and unlimited quick studies, but only the first 15 self-recruited responses per test are viewable. Growth costs $199 a month, or $165 billed annually, and panel responses cost about $1 per participant-minute. Figma's guide adds that Lyssna's panel holds 690,000+ people in 120+ countries, with 395+ filters and AI follow-up questions.

**Maze has the best Figma link but the tightest ceiling.** A third-party read of its pricing page on October 12, 2026 says US buyers see only Free (5 seats, 1 study a month) and a custom Enterprise plan ([User Insight](https://userinsight.ai/blog/maze-pricing), [Checkthat](https://checkthat.ai/brands/maze/pricing)). Its AI moderator and interviews are Enterprise-only, so one study a month is the hard limit for a plan built on many small rounds.

**Useberry is the cheapest paid upgrade.** Free gives 10 responses a month, and Growth costs $79 a month, or $67 billed annually, with deep Figma import ([G2](https://www.g2.com/products/useberry/pricing)). G2 lists 50% off Growth for students, which brings it to about $33 to $40 a month.

**Moderated-session tools cost money you don't need to spend.** Lookback, the best-known one, has no free plan; Freelance costs $299 a year for 10 sessions. Your own video calls do the same job for free, with recordings kept on your computer.

**The rest are too costly or unconfirmed.** Userbrain's free plan is described inconsistently ([Userbrain](https://www.userbrain.com/blog/best-ux-research-tools/), [UXtweak blog](https://blog.uxtweak.com/userbrain-pricing/)), Optimal Workshop starts at about $199 a month, and PlaybookUX charges from $59 per participant ([UXtweak blog](https://blog.uxtweak.com/playbookux-vs-usertesting/)). Trymata lets participants sign a custom NDA, which matters for confidential studies, but its price is unconfirmed. UserTesting, now merged with UserZoom, costs about $149 a session with a 10-session minimum.

**Free analytics cover the live app.** Microsoft Clarity is free with up to 100,000 sessions a day and 30-day recordings, but Microsoft's data terms rule it out for confidential products ([Clarity Insights](https://www.clarity-insights.com/blog/what-is-microsoft-clarity.html)). Hotjar's free tier shrank in 2026 for new accounts ([Koji](https://www.koji.so/blog/hotjar-vs-microsoft-clarity-2026)). PostHog is open source, its free cloud tier includes 5,000 recordings a month, and it can be self-hosted, which keeps data on your own server ([Volument](https://volument.com/blog/posthog-pricing-2026-plans-costs-and-how-billing-really-work/)).

**AI-moderated interviews are poor value for you now.** Maze's AI moderator is Enterprise-only, Great Question costs $129 per seat a month with no free plan ([Great Question](https://www.greatquestion.com/blog/user-interviews-alternatives)), and Outset and Listen Labs are sales-led. Figma's guide notes Useberry's AI sentiment summaries and Lookback's Eureka assistant for transcripts and themes. All of these send your content through outside AI models, which is acceptable for Ambition's public work and ruled out for confidential studies.

**For a developer and crypto tool, bring-your-own beats panels.** No mainstream panel reliably targets Web3 developers. The tools that fit best are the ones that let you invite your own participants free (UXtweak, Lyssna, Useberry and Figma links) plus analytics developers already trust (PostHog).

## 4. Recruiting cheaply

**Your build-in-public audience is the cheapest and best-matched pool you have.** Each module's reader challenge can double as a study link, such as "Take this 3-minute tree test of Ambition's docs." Sui developer communities and Discord, Farcaster, agent-builder Discords, hackathon alumni and Quantic classmates add crypto-native and crypto-novice perspectives. Once its snippet is on your site, UXtweak's onsite recruiting widget invites docs visitors for free.

**Paid panels are poor value for finding crypto developers.** User Interviews charges $49 per B2C or $98 per B2B session, with incentives billed on top ([pricing](https://www.userinterviews.com/pricing)). Prolific adds a 42.857% fee to participant rewards for companies, or 33.3% for academic accounts, and requires at least $8 an hour, with $12 recommended ([Prolific](https://researcher-help.prolific.com/en/articles/445239-what-is-your-pricing)). Respondent reportedly charges about $40 per B2C and $80 per B2B session, a figure I did not recheck.

**Fair thank-yous matter more than big ones.** For developers in a build-in-public community, a $20 to $25 gift card, public credit in a post, early access or a contributor badge on GitHub is a reasonable mix. Avoid paying in real crypto, because it raises tax and identity-check questions and blurs testing with promotion.

**Five users per round is enough, if you run many rounds.** Nielsen Norman Group advises ["testing no more than 5 users and running as many small tests as you can afford"](https://www.nngroup.com/articles/why-you-only-need-to-test-with-5-users/), since each extra user reveals fewer new problems. Distinct user groups each need their own 3 to 4 participants, and quantitative studies need about 40.

Ambition has two groups, AI builders new to crypto and crypto-native developers, so plan 3 to 5 of each per round.

## 5. Web3 and developer-tool specifics

**Wallets, faucets and signing break most unmoderated tests, so take them out of the test until you are testing them.** There are three ways to do that, in the order the plan uses them. Each removes a step that has nothing to do with the question being asked.

1. **Simulate the money in a Figma Make prototype** (modules 3 to 6). The prototype shows a balance, a confirmation and a final status with no wallet, so any tester can finish the task unmoderated.
2. **Pre-fund wallets for moderated sessions** (modules 5 to 10). [Circle's faucet](https://faucet.circle.com/) gives 20 test USDC on Sui's test network per address every 2 hours with no account. [Sui's faucet](https://docs.sui.io/guides/developer/getting-started/get-coins) gives test SUI but limits how often each address may ask, so fund wallets the day before.
3. **Use zkLogin and sponsored transactions for unmoderated tests of the live app** (modules 7 to 11). [zkLogin](https://docs.sui.io/concepts/cryptography/zklogin) lets people create a Sui wallet by signing in with Google, Facebook, Twitch or Apple on the test network, and Ambition's gas station pays their fees through [sponsored transactions](https://docs.sui.io/concepts/transactions/sponsored-transactions), so testers need no extension and no test SUI.

**The confirmation screen deserves the most testing.** MetaMask's design team found that [70 to 90% of all user actions](https://github.com/MetaMask/Design/issues/80) happen on or around the Confirm screen. That makes Ambition's spend-confirmation dialog the highest-leverage screen, and the first one to build in Figma Make.

**Use the published web3 heuristics as your review checklist.** ethereum.org lists [seven web3 heuristics](https://ethereum.org/developers/docs/design-and-ux/heuristics-for-web3/), such as "feedback follows action" and "understandable terminology", to use alongside Nielsen's ten. A [systematic review](https://arxiv.org/pdf/2204.10857) found that crypto wallets generally lack proven good usability and that hardly any studies test improvements. A widely repeated claim that 55% of users abandon wallet setup has no traceable source, so don't cite it.

**Test the developer side with a timed first task.** Give a developer the README and ask them to make an agent wallet pay Ambition's test paid service while thinking aloud and sharing their screen and terminal. Time it, count the times they get stuck, and note every error message they hit. Then show them a raw error and ask what they would do next, which tests the message itself.

## 6. Ethics and consent

**Tell every participant what you record and why, then get their consent on the recording.** Say what you are testing, what you capture (screen, voice, face), where it is stored, how long you keep it, and that they can stop at any time. Under GDPR, consent must be freely given and specific, and participants can ask to see or delete their data. CCPA mainly covers businesses above revenue or data thresholds, so it likely doesn't apply yet, but following GDPR practice covers you either way.

**Ask Quantic in writing whether your capstone studies need ethics review.** In the US, review rules cover research meant to produce generalizable knowledge, while testing only to improve a product is usually treated as quality improvement. Because Ambition is your capstone and you may publish findings, the school decides. I found no public Quantic policy on this, so this is an inference from general US practice.

**Pay fairly and never for praise.** Pay comparable amounts within each round, never tie payment to positive feedback, and treat Prolific's $12 an hour as the floor for any paid panel work.

# Part 2: The usability-testing plan

## Ambition: seven phases to Ambition version 1

Ambition's plan runs seven phases across modules 1 to 12 and ends with Ambition version 1 at rung 3. Each phase starts when its module does, so the plan carries no dates until the capstone course sets them. The Figma Make prototype moves the first unmoderated test of a complete payment from modules 10 to 11 up to modules 4 to 5. Following Figma's Predict step, every human round starts only after an AI audit of contrast, hierarchy, dead ends and error states passes.

The modules 4–5 row is the change from the first plan: testers complete a payment with simulated money on the Make prototype six modules before zkLogin sign-in exists.

| Modules | Method | Tool | Participants | Cost | What it answers |
| --- | --- | --- | --- | --- | --- |
| 1–2 | Open card sort of glossary and module names | UXtweak Free | 10 LinkedIn readers | $0 | Do readers group and name Ambition's ideas the way the docs do? |
| 3–4 | Tree test of docs navigation; build the Make prototype of the spend confirmation, limit editor and spend meter with simulated test money; AI audit | UXtweak Free; Figma Make; Carbon code audit and contrast checker | 10 | $0 | Can readers find the quickstart and the limit settings? Does the prototype pass the audit? |
| 4–5 | First-click and 5-second tests on prototype screens; unmoderated "Send 5 test USDC" task on the Make prototype | Lyssna Free (15), UXtweak Free (3), Figma view-only link | 15–18 | $0 | Do people see the amount, recipient, network and finality before they confirm? |
| 5–7 | Moderated think-aloud, round 1, on the prototype and the quickstart, with a timed first task | Video call recorded locally; FigJam for observers and notes | 5 developers | $0–$125 | Where do developers get stuck on the way to a first payment? |
| 7–10 | Live testnet app with session replay and an in-app survey; moderated round 2 with pre-funded or zkLogin wallets; AI audit first | PostHog Free or Clarity; Circle faucet; zkLogin and sponsored transactions | 5 developers plus all visitors | $0–$125 | Do round 1's fixes hold up with real test transactions? |
| 10–11 | System Usability Scale (SUS) survey after tasks; unmoderated website test once zkLogin sign-in is live | PostHog surveys or Google Forms; UXtweak | 10–20 | $0 | How usable is Ambition overall, as one score for the rung-3 review? |
| 12 | Fix round, quick re-test of the top 3 issues, findings published with module 12 | Same tools | 3–5 | $0 | Did the top problems go away? |

Each round mixes the two groups, AI builders new to crypto and crypto-native developers, with 3 to 5 of each in the moderated rounds. An optional synthetic-user pass can check structure before rounds 1 and 2, but it never replaces a participant. Each round's notes and decisions go into a FigJam board and the design system's decision log, and the findings are published with that module's notes.

## Budget

The plan works at $0, and money mainly buys fairer thank-yous rather than better tools.

| Budget | What you get |
| --- | --- |
| $0 | UXtweak Free, Lyssna Free, Figma Make prototypes and FigJam on your Education plan (if Make is included), PostHog Free or Clarity, free video calls, a Google Forms SUS survey, the Circle faucet, and volunteers thanked with public credit and early access |
| Under $100 | Everything above, plus $20 gift cards for 4 developers in the hardest round ($80), or one month of Useberry Growth at the student discount (about $33 to $40) if the 10-response cap blocks you |
| Under $500 | Everything above, plus $20 for each of 10 developers across 2 rounds ($200), and one month of UXtweak Business (about €92 to $107) during modules 7 to 10 unless the student discount makes it free |

## First actions

- [ ] Email UXtweak and Useberry for student access, naming Quantic and your capstone
- [ ] Check whether your Figma Education plan includes Figma Make, and how many AI credits it allows
- [ ] Ask Quantic in writing whether capstone usability studies need ethics review
- [ ] Fill in the [participant consent form](participant-consent-form.md) and adapt its recording notice
- [ ] Put the card sort into module 1's reader challenge
- [ ] Build the spend-confirmation flow in Figma Make with simulated test money
- [ ] Plan the zkLogin and gas-station build for modules 7 to 10

## Caveats

Several prices couldn't be confirmed on vendors' live pages: UXtweak's Business price, Maze's US Starter plan, the free plans of Userbrain and Optimal Workshop, and the prices of Loop11, Trymata, TestingTime, Respondent, Outset and Listen Labs. Many comparison figures come from competitors' blogs, which have reasons to make rivals look expensive. UXtweak's Business response allowance and Hotjar's free plan both changed recently, and PostHog's free survey allowance is reported as both 1,500 and 250.

Figma's guide is undated and lists no prices. I couldn't confirm that your Education plan includes Figma Make, how many AI credits it allows, or whether a Make prototype can carry UXtweak's snippet. Attention Insight's 96% accuracy figure is its own claim. Every AI-training and data-location statement in this doc is a vendor claim, so verify each price at checkout and recheck before you spend.

## Sources

- [Figma: AI usability testing](https://www.figma.com/resource-library/ai-usability-testing/)
- [UXtweak: Pricing](https://www.uxtweak.com/pricing/)
- [UXtweak: Website usability testing tool](https://www.uxtweak.com/website-usability-testing-tool/)
- [UXtweak: Launching a website testing study](https://www.uxtweak.com/help/website-testing-setup/launching-a-website-testing-study/)
- [UXtweak: Privacy by design](https://www.uxtweak.com/legal/privacy-by-design/)
- [UXtweak: GDPR compliance](https://www.uxtweak.com/legal/gdpr-compliance)
- [UXtweak: Participant recruitment](https://www.uxtweak.com/user-participant-recruitment/)
- [UXtweak Chrome extension](https://chromewebstore.google.com/detail/uxtweak/dagniddgipkffcehffkjgbdobhldacgl?hl=en)
- [G2: UXtweak reviews](https://www.g2.com/products/uxtweak/reviews)
- [Capterra: UXtweak](https://www.capterra.com/p/193026/UXtweak/)
- [Makerstack: UXtweak review](https://makerstack.co/reviews/uxtweak-review/)
- [Crozdesk: UXtweak pricing](https://crozdesk.com/software/uxtweak/pricing)
- [Lyssna: Plan and pricing overview](https://help.lyssna.com/en/articles/4953377-plan-and-pricing-overview)
- [Koji: Lyssna pricing 2026](https://www.koji.so/blog/lyssna-pricing-2026)
- [User Insight: Maze pricing](https://userinsight.ai/blog/maze-pricing)
- [Checkthat: Maze pricing](https://checkthat.ai/brands/maze/pricing)
- [G2: Useberry pricing](https://www.g2.com/products/useberry/pricing)
- [Userbrain: Best UX research tools](https://www.userbrain.com/blog/best-ux-research-tools/)
- [UXtweak blog: Userbrain pricing](https://blog.uxtweak.com/userbrain-pricing/)
- [UXtweak blog: PlaybookUX vs UserTesting](https://blog.uxtweak.com/playbookux-vs-usertesting/)
- [UXtweak blog: Userlytics vs UserTesting](https://blog.uxtweak.com/userlytics-vs-usertesting/)
- [Listen Labs: UserTesting alternatives](https://listenlabs.com/articles/best-usertesting-alternatives/)
- [Great Question: User Interviews alternatives](https://www.greatquestion.com/blog/user-interviews-alternatives)
- [Clarity Insights: What is Microsoft Clarity](https://www.clarity-insights.com/blog/what-is-microsoft-clarity.html)
- [Koji: Hotjar vs Microsoft Clarity 2026](https://www.koji.so/blog/hotjar-vs-microsoft-clarity-2026)
- [Volument: PostHog pricing 2026](https://volument.com/blog/posthog-pricing-2026-plans-costs-and-how-billing-really-work/)
- [User Interviews: Pricing](https://www.userinterviews.com/pricing)
- [Prolific: Pricing](https://researcher-help.prolific.com/en/articles/445239-what-is-your-pricing)
- [Nielsen Norman Group: Why you only need to test with 5 users](https://www.nngroup.com/articles/why-you-only-need-to-test-with-5-users/)
- [Nielsen Norman Group: Unmoderated user testing tools](https://www.nngroup.com/articles/unmoderated-user-testing-tools/)
- [Circle: Testnet faucet](https://faucet.circle.com/)
- [Sui documentation: Get coins](https://docs.sui.io/guides/developer/getting-started/get-coins)
- [Sui documentation: zkLogin](https://docs.sui.io/concepts/cryptography/zklogin)
- [Sui documentation: Sponsored transactions](https://docs.sui.io/concepts/transactions/sponsored-transactions)
- [npm: @coinbase/cdp-sdk](https://www.npmjs.com/package/@coinbase/cdp-sdk)
- [MetaMask Design: Confirmation screen issue](https://github.com/MetaMask/Design/issues/80)
- [ethereum.org: Heuristics for web3](https://ethereum.org/developers/docs/design-and-ux/heuristics-for-web3/)
- [arXiv: Systematic review of cryptocurrency wallet usability](https://arxiv.org/pdf/2204.10857)
