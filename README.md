# GroupDNA 🧬

A WhatsApp group chat analyzer built with **only core Python and NumPy** — no pandas, no matplotlib, no external analysis libraries. This was a deliberate constraint: the goal was to understand how raw text data gets cleaned, structured, and aggregated *before* reaching for a library that does it for you.

This was my first minor project during my Data Science course at UNLOX.

## What it does

The notebook takes a raw exported WhatsApp chat (`.txt`) and runs it through 7 features:

1. **Chat Parser** – converts raw exported text into structured message objects, handling multi-line messages, media placeholders, deleted messages, and system messages
2. **Group Overview** – ranks participants by message count and share of total conversation
3. **Busiest Day & Hour** – finds peak activity windows across the whole chat history
4. **Activity Heatmap** – builds a `(participants × 24-hour)` NumPy matrix and renders it as shaded ASCII output
5. **Top Words** – word frequency ranking with a custom, manually built stop-word filter
6. **Response Speed & Silent Streaks** – uses `datetime` deltas to find fastest/slowest repliers and longest inactivity gaps per person
7. **Personality Archetypes** – a rule-based scoring and threshold system that labels each participant (e.g. "Night Owl", "Group Mom", "Spammer", "Ghost") based on behavioral signals in their messages

## Example output

```
GROUP OVERVIEW
----------------------------------------
Total messages: 3142
Participants  : 6

Busiest hour: 18:00 - 19:00 (246 messages)

ACTIVITY HEATMAP (messages by hour, shown every 3 hours)
           00  03  06  09  12  15  18  21
 Person1   ▒  ▒  .  .  .  .  .  .
 Person2   .  .  .  ░  █  ▒  ▒  ░
```

## Tech used

- **Python** — parsing, dictionaries, string handling on messy real-world text
- **NumPy** — building and querying the 2D activity matrix
- **datetime** — timestamp parsing and time-based aggregation

No pandas, no matplotlib, no NLP libraries — everything here is built from loops, dictionaries, and NumPy arrays on purpose, as a way to learn the fundamentals before automating them away.

## Known limitations

This is a learning project, and I'm sharing it as one — not as a polished tool. A few things I'd do differently with more time:

- The stop-word list is manually curated, not a standard NLP library list
- Personality archetypes are rule-based scoring with fixed thresholds, not a trained model — this was intentional, to understand the logic before reaching for machine learning
- No regex used for parsing; string splitting only
- No proper data visualization (charts) — output is text/ASCII only

## What's next

Rebuilding this with **pandas** for the data handling and adding proper charts (matplotlib/seaborn), to compare the from-scratch approach against the library-driven one.

## Data privacy

The sample chat data used here has been anonymized — names in the code/output are not the real participants' names.

## Author

**Piyush Sable**
Data Science course, UNLOX
