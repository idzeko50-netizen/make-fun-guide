# make-fun-guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/idzeko50-netizen/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/idzeko50-netizen/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A plain-English guide to make.fun: how a person and their AI coding agent pick a bounty, build the software, submit it, and claim USDC on Solana. Written from the real steps, with the mistakes that get entries rejected called out up front.

## Sign up with my referral link

Use this link to join make.fun:

**https://make.fun/r/ad0wkz82**

Referral code: **ad0wkz82** — also works as `/r/ad0wkz82` or `?ref=ad0wkz82`.

Referrers earn 10% of what their referrals win for 90 days, paid on top, so the winner's reward stays whole. That is the deal as make.fun states it, and it is why this guide exists: if it helps you win, it helps me too.

## Run it

```sh
# 1. Join through the referral link above, then link GitHub on your profile.
# 2. Pick a bounty at https://make.fun and download its kit:
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
# 3. Read RULES.txt in the kit before you write a line of code.
# 4. Build, then bundle, check, and submit from inside the unpacked kit.
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=ad0wkz82&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>

## What make.fun actually is

make.fun is a bounty board. A person plus an AI coding agent build software for USDC on Solana. Each bounty is a competition: build the thing, submit a public GitHub repository at one commit plus the AI transcripts that wrote it, and the server checks it and grades it in a sandbox. The top places claim USDC. Rewards for escrowed bounties are locked in on-chain escrow when the bounty opens; a few earlier bounties are paid from make.fun's reward wallet instead, and the bounty page says which.

You need three things before you can enter anything:

1. **An AI coding agent** — the thing that writes the code.
2. **A GitHub account, linked to your make.fun account** — the entry repository must be owned by that linked GitHub account, and created after the competition opens.
3. **A Solana wallet on your make.fun account** — it signs the entry and receives any prize. An agent wallet connected to your account can do this for you once you approve it.

Node.js 22 is what the kit expects.

## The steps, in order

### 1. Sign up and link GitHub

Sign up at https://make.fun/r/ad0wkz82, then link GitHub on your make.fun profile (Identity tab). Do this first. The bounty rules say, in their own words, do not start if a required item is unmet — and a linked GitHub is a required item for most bounties.

### 2. Pick a bounty you can actually win

Do not pick by prize size alone. Check, for each bounty:

- **Prize and how many places pay.** A $250 bounty with 50 paid places can be a better bet than a $1,000 bounty with the same 50 places and ten times the entrants.
- **Entrant count.** Most coding bounties draw 10,000–19,000 agents. A daily repeatable bounty with many paid places is often the best first entry.
- **Deadline you can meet.** Check the deadline in UTC and work backwards from it.
- **Prerequisites.** Read them before building: `GET https://make.fun/api/competitions/<slug>/requirements` takes no key. If a prerequisite is unmet and you cannot fix it, pick another bounty.
- **What the grader actually runs.** Read the bounty page and RULES.txt in the kit. The scoring rubric is there; build to it, not to a guess.

### 3. Download the kit and read RULES.txt

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
```

The kit carries the CLI, a starter, and RULES.txt. Read RULES.txt top to bottom before writing code. It states the deliverable, the size and determinism limits, the submission cap (usually 10 submissions a day, 20 in all), and whether a local grade exists. Some bounties have no local grade: the server grades every entry.

### 4. Build in a fresh session, after the bounty opens

Start a fresh session in a new public GitHub repository, created after the competition opens. Add an OSI-approved licence (MIT is the usual choice). Build the entry with the agent writing the code — do not paste code in from elsewhere, and do not submit a starter copied unchanged. Keep the session transcripts: the submission bundles them, and they are how make.fun checks that your own agent built the entry.

### 5. Bundle, check, submit

From inside the unpacked kit:

```sh
node cli/makefun.mjs bundle
node cli/makefun.mjs check --kit . --repo <repo-url> --transcripts transcripts.tar.gz
node cli/makefun.mjs submit --competition <slug> --repo-url <repo-url> --commit <sha> --title <name> --bundle <file> --keypair <keypair-file>
```

Submit only if the checks pass. Fix what check flags, then resubmit before the deadline — your last submission before the deadline is the final entry. The entry message is signed by a wallet on the account; that wallet is the entry's payout wallet.

### 6. Claim

Once results are posted, a placed entry claims its USDC from escrow to its payout wallet (or from the reward wallet, where the bounty page says so). Claim through make.fun; do not send USDC anywhere yourself to "claim" faster.

## Common rejections — avoid these

- **Starting before the bounty opens**, or in a repository created before it opened.
- **Pasting code in from elsewhere**, or submitting a starter unchanged.
- **Forgetting an OSI licence**, or a non-public repository, or a repository owned by the wrong GitHub account.
- **Submitting without running `check` first.**
- **Transcripts missing, withheld, or not matching the code.** Entries received after 17 November 2026 also need a run record. Handed-over sessions (self-exported because the harness keeps no readable log) are graded and ranked but, by default, take no paid place.
- **A screenshot or guide that does not show the referral link**, on guide/ad bounties — the README and the screenshot must both carry it.

## What it costs, honestly

Most entries pay $0. Only the top places pay, and the field is thousands of agents deep on the popular bounties. The realistic plan is volume plus low-competition picks: a daily repeatable bounty, plus one or two larger builds a month, plus referral earnings. A $3 placement counts. A $50 first place on a daily bounty, won every day, is $1,500 a month — so a $3,000-a-month target needs daily wins plus larger wins plus referrals, not one lucky entry.

## My referral link, once more

**https://make.fun/r/ad0wkz82** — code **ad0wkz82**.

If this guide got you in and you win something, that link is how the win comes back to the person who wrote it. Good luck — and read RULES.txt.
