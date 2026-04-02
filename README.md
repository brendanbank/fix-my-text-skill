# fix-my-text — Claude Code Skill

A [Claude Code skill](https://docs.anthropic.com/en/docs/claude-code/skills) that corrects spelling, grammar, and sentence structure while keeping your words, tone, and voice exactly as you wrote them.

## Background

I'm dyslexic. I have a lot to say and I know how I want to say it, but the mechanics of spelling and punctuation get in the way. Standard "fix my text" prompts tend to rewrite everything in clean, formal, AI-sounding language — and then it no longer sounds like me.

I built this skill so Claude corrects the mechanics but leaves my voice alone. If I wrote "stuff", it stays "stuff". If I wrote a casual run-on, it gets cleaned up minimally. The goal is that after correction, the text still reads like something I actually wrote.

It works especially well for:
- Emails and Slack messages
- Quick notes and memos
- Any text where the writing is yours but the spelling got away from you

## What it does

- Fixes spelling (including common dyslexic patterns: letter swaps, missing letters, doubled letters)
- Fixes grammar (subject-verb agreement, tense, articles, punctuation)
- Capitalises correctly after full stops, proper nouns, and "I"
- Formats greetings properly (e.g. `hi john, just wanted...` → `Hi John,\nJust wanted...`)
- Splits run-ons at natural pauses
- Removes clearly unintentional word repetition

## What it does NOT do

- Does not swap your words for fancier synonyms
- Does not restructure sentences that already make sense
- Does not add formality to casual text
- Does not add greetings, sign-offs, or filler phrases you didn't write
- Does not use the em dash (—) — a telltale sign of AI-generated text

## Output format

1. The corrected text first — clean, ready to copy, no preamble
2. A horizontal rule separator
3. A short `Changes:` log listing what was fixed — useful for learning your own patterns over time

If something is ambiguous (a word could go two ways), it flags it rather than guessing.

## Installation

### Claude Desktop App and Mobile App

1. Download [fix-my-text.skill](https://github.com/brendanbank/fix-my-text-skill/releases/download/v0.0.1/fix-my-text.skill)
2. Open Claude
3. Go to **Customize > Skills**
4. Click the **+** button, then **+ Create skill**
5. Select **Upload a skill**
6. Upload the downloaded `fix-my-text.skill` file

The skill syncs across all your devices through your Anthropic account.

**Prerequisite:** Make sure **Code execution and file creation** is enabled in **Settings > Capabilities**.

### Claude Web (claude.ai)

Same steps as above:

1. Download [fix-my-text.skill](https://github.com/brendanbank/fix-my-text-skill/releases/download/v0.0.1/fix-my-text.skill)
2. Go to [claude.ai](https://claude.ai)
3. Go to **Customize > Skills**
4. Click the **+** button, then **+ Create skill**
5. Select **Upload a skill**
6. Upload the downloaded `fix-my-text.skill` file

### Claude Code (terminal)

```bash
mkdir -p ~/.claude/skills/fix-my-text
curl -L https://github.com/brendanbank/fix-my-text-skill/releases/download/v0.0.1/fix-my-text.skill \
  -o /tmp/fix-my-text.skill
unzip -o /tmp/fix-my-text.skill -d ~/.claude/skills/
```

## Usage

Trigger phrases that activate the skill automatically:

- `/fix-my-text`
- "fix this"
- "correct this"
- "clean up my text"
- "check my spelling"
- "proofread this"
- "fix my email"
- "does this make sense"
- "can you fix the grammar"

Or just paste text with spelling issues and ask for help with it.

## Example

**Input:**
```
hey can you send me the docuemnt from yesturday i need to reveiw it befor the meating tomorow. also the clinet wants to now about the new fetures we diskussed
```

**Output:**
```
Hey can you send me the document from yesterday. I need to review it before the meeting tomorrow. Also the client wants to know about the new features we discussed.

---

Changes: Fixed spelling: docuemnt → document, yesturday → yesterday, reveiw → review, befor → before, meating → meeting, tomorow → tomorrow, clinet → client, now → know, fetures → features, diskussed → discussed. Capitalised: hey → Hey, also → Also, i → I. Added periods.
```

## License

BSD 2-Clause
