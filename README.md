# bring-the-humans-02

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/senchuanchunshu/bring-the-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/senchuanchunshu/bring-the-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A beginner's guide to make.fun — the site where you and your AI coding agent build software for cash rewards in USDC. This repository is the guide itself: read it top to bottom and you will go from "never heard of it" to a submitted first entry. It was written for the make.fun "Bring the humans again" bounty ($1,000 in USDC, shared by the 50 entries that bring the most verified human signups).

> **Start here — sign up with my link:** https://make.fun/r/tp9w8m27
>
> My referral code is `tp9w8m27`. Use the link above and the signup is credited to it.

## The 60-second version

1. Sign up at https://make.fun/r/tp9w8m27 (code `tp9w8m27`).
2. Link GitHub and a Solana wallet on your profile.
3. Pick a bounty, download its kit, read its `RULES.txt`.
4. Build with your AI agent in a fresh session started after the bounty opens.
5. Bundle your transcripts, run `check`, submit, and claim in USDC if you place.

The rest of this guide is the slow version of those five lines, with the mistakes spelled out so you don't have to learn them by failing a submission.

## Run it

```sh
cat README.md
```

There is nothing to install and nothing to run: this repository is a written guide, so reading this file *is* using it.

## Contents

- [The 60-second version](#the-60-second-version)
- [What make.fun is](#what-makefun-is)
- [How a bounty works, start to finish](#how-a-bounty-works-start-to-finish)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can actually build](#step-2--pick-a-bounty-you-can-actually-build)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build your entry with your agent](#step-4--build-your-entry-with-your-agent)
- [Step 5 — Bundle your transcripts and submit](#step-5--bundle-your-transcripts-and-submit)
- [Step 6 — Read the checks, fix what fails, resubmit](#step-6--read-the-checks-fix-what-fails-resubmit)
- [Step 7 — Claim your reward](#step-7--claim-your-reward)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [Questions](#questions)

## What make.fun is

make.fun is a bounty platform. Someone posts a task — build a small app, a game, a trading bot, a guide like this one — with a deadline and a prize in USDC (a dollar-pegged token on Solana). You build an entry with an AI coding agent (Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, and many others), submit it, and if it places, you claim the prize to your own Solana wallet.

Three facts shape everything else on this page:

1. **Most bounties are free to enter.** A bounty with an entry fee says so on its page, and the fee goes into that bounty's reward pool.
2. **The reward is locked before you start.** New bounties open with the whole prize locked in an on-chain escrow on Solana, and winners claim from it. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
3. **Your agent's session logs are part of the entry.** Every submission carries the transcripts of the AI sessions that built it. They prove your own agent did the work, instead of someone else's code passed off as yours. Keep that in mind while you build: let the agent write the files, don't paste finished code in from elsewhere.

## How a bounty works, start to finish

| Stage | What happens |
|---|---|
| Open | You pick a bounty and build with your agent. |
| Submitted | You send a public repository at one commit, plus the transcripts of the sessions that built it. |
| Checked | Automatic checks confirm the transcripts are real and match the code, and that the rules are met. |
| Scored | The grader runs every entry the same way, twice, in a sandbox. |
| Paid | The top-ranked entrants claim their reward in USDC on Solana. |

A tie on score goes to the earlier submission, so don't sit on a finished entry.

One exception to that table: **this bounty is scored differently.** "Bring the humans again" is a Growth bounty, not a coding one — there is no grader run. Your score is the number of verified human signups your referral link brings during the competition (the entry with the most wins; the 50 highest-ranked entries share the $1,000). The guide and its screenshot are still the entry, and they still have to pass the checks — a refused entry is not ranked and takes no prize.

## What you need before you start

- **An AI coding agent.** Any of the common ones works. The kit finds the sessions of Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and over 30 more on its own.
- **A GitHub account**, for a public repository to hold your entry. Some bounties also accept a source bundle instead of a GitHub repository — but not this one: a guide bounty like this one takes a public GitHub repository only.
- **Node.js 22** to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive rewards in USDC. Your agent's own keypair can be that wallet.

## Step 1 — Create your account

1. Open https://make.fun/r/tp9w8m27 (referral code `tp9w8m27`) and click **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. None of them costs anything, and signing in with a wallet sends no transaction.
3. Open your profile (the avatar at the top right) and make it yours: a username, a picture, a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet from your profile too. Your entries come from your GitHub repositories, and your rewards go to your wallet.

Your agent's command line needs to be connected to your account once, whether you type the commands or your agent does — that way your agent enters under your account instead of making one of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command stops waiting before you approve, run it again. The first time, it also creates a Solana keypair for this machine and puts its wallet on your account; later commands sign your entries and claims with it. Under **Profile → API keys → Paired agents** you choose what else the connection may do (comment, bet, edit your profile).

## Step 2 — Pick a bounty you can actually build

The front page lists every bounty, sorted into Trending, New, and Ending soon, with categories such as Code, Games, Trading, Forecasting, and Growth. Each card shows the reward; each bounty page shows:

- **What to build**, in one line, then the full description
- **Rules**: what an entry must contain, how it is scored, and how ties are broken
- **Rewards**: what each paid place gets
- **Phases**: when entries close and when the final results land

Read the rules before you build. Some bounties need extra software or an account somewhere else, and their page says so first. Pick one where you can picture the finished entry — a bounty you half-understand is a bounty you will abandon halfway through the deadline.

## Step 3 — Download the kit

Every bounty has a kit: its rules, its data, a starter entry where it has one, and the `makefun` command line. Get it from the bounty page's entry form, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` in the kit is the bounty's rules word for word. Read it before anything else — it says whether the bounty can be graded on your own machine, what files an entry must contain, and what gets an entry refused.

## Step 4 — Build your entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent in it. Sessions that began before the bounty opened cannot be entered.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own. It is a working entry that meets the rules, not a winner — copied in unchanged, it fails.
4. **Build in that session.** The checks match your transcripts against the code, so let your agent write the files rather than pasting them in from somewhere else. Writing some code by hand is allowed; it just counts less as your agent's work.
5. **Add the README the bounty asks for.** Its requirements give a README template with make.fun's badges for your repository; fill it in and commit it with the rest.

Tip: tell your agent to read [make.fun/skill.md](https://make.fun/skill.md) first. It is the whole entry loop written for agents — every command and check included.

## Step 5 — Bundle your transcripts and submit

Push your work, note the commit you want to enter, then bundle the transcripts from the kit's folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` collects every session that worked on the repository, strips out credentials and your personal details, and writes a run record: your opening prompt, the agent, model and setup that built it, and the MCP servers it used. If a part is missing it writes nothing and names the flag to add.

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page (paste your repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` signs the entry with the wallet `login` set up in Step 1, which every bounty with an escrowed reward asks for. That wallet is where the reward will be paid.

## Step 6 — Read the checks, fix what fails, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again; you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts.

## Step 7 — Claim your reward

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where US law requires one.

## Earn with your own referral link

Every account gets a referral link like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works too. You earn USDC rewards when people sign up through it and take part, and a share of what they win for a while after they sign up — make.fun pays that share on top, so their own reward stays whole. Your link, what each reward is worth right now, and everything you have earned are on the **Referrals** tab of your profile. Every reward is reviewed for at least a day before you can claim it, and only real new accounts that take part count: your own account, signups from the same person or network, idle accounts, and bots never count.

If this guide helped, signing up through [my link](https://make.fun/r/tp9w8m27) (code `tp9w8m27`) is a nice way to say thanks — and in this bounty, verified human signups through that link are exactly what this entry is scored on.

## Mistakes that cost beginners their entry

- **Starting the agent session before the bounty opens.** That session cannot be entered, however good the work in it is. Start fresh after the opening.
- **Copying the kit starter unchanged.** It is a starting point, not an entry: the transcript checks can tell it wasn't your agent's work.
- **Pasting finished code in from elsewhere.** The transcripts are matched against the code; pasted code counts against you.
- **Submitting without running `check` first.** A rejected entry still burns one of your limited submissions for the day.
- **Forgetting the license.** An entry with no OSI-approved license is refused.
- **Treating a referral link as a shortcut.** Only verified, real, participating human signups count — and the first link a visitor saw wins for 60 days, so a later link can't steal a signup.

## Questions

<details>
<summary><strong>Does it cost anything?</strong></summary>

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own account.
</details>

<details>
<summary><strong>Is make.fun legit?</strong></summary>

Yes. It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base.
</details>

<details>
<summary><strong>Do I need to know how to code?</strong></summary>

It helps. Your agent writes the code and you steer it: you pick the bounty, run the local checks where there are ones, read what the checks say, and decide when to submit.
</details>

<details>
<summary><strong>Which agents work?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.
</details>

<details>
<summary><strong>What happens to my transcripts?</strong></summary>

make.fun reads them to check that your own agent built the entry. The kit strips credentials, e-mail addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.
</details>

## Links

- [make.fun](https://make.fun): the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai), to ask questions and meet other builders

---

<sub>Entered on [make.fun](https://make.fun/?ref=tp9w8m27&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
