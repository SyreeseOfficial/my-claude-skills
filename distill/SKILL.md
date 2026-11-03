---
name: distill
description: Make a text file more concise without losing any detail. Removes filler, repetition, and padding while keeping every fact, name, number, step, caveat, and nuance intact. Rewrites at 5th grade reading level. Uses beautiful markdown formatting with tables, bold, italics, and visual hierarchy for easy scanning. Works on any text file; markdown is the primary use. Trigger when the user says "distill", "condense", "tighten", "make this more concise", "cut the filler", "compress this file", or "/distill" — and points at a file. NOT a summary: nothing is dropped, only reworded shorter.
---

# Distill

Rewrite a text file so it is **much shorter** to read but carries **every** detail. Remove filler, not information. Make it *beautiful* and enjoyable to read through smart markdown.

**Keep:** Facts, names, numbers, dates, URLs, code, versions, conditions ("only if"), exceptions, warnings, reasons ("because"), qualifiers ("usually", "never"). Every claim in the source must survive.

**Cut:** Throat-clearing ("It's worth noting"), repetition, padding ("in order to" → "to"), hedging ("very", "really"), empty transitions ("That being said"), long wind-ups.

## Process

1. Read the whole file. Understand every point before cutting.
2. Use 5th grade level: short words, short sentences. Replace "utilize" → "use", "subsequent" → "after".
3. **Use rich markdown formatting strategically:**
   - **Tables** for comparisons, attributes, specifications, or anything with 2+ related pieces of data
   - ***Bold and italic*** for emphasis, important terms, keywords
   - `Code blocks` for commands, files, technical terms, examples
   - **Nested lists** with proper hierarchy instead of flat prose
   - Blockquotes for key takeaways, notes, or important warnings
   - Horizontal rules to separate major sections visually
   - **Unordered lists** instead of comma-separated items when possible
4. Rewrite section by section, keeping order and headings unless collapsing loses nothing.
5. Convert to tighter forms: lists → bullet or table; "X does A, and X also does B" → one sentence or structured list.
6. Preserve links, emphasis, code/commands verbatim.
7. Verify: every fact, number, name, step, condition, and caveat from the source appears in the output.

## Markdown Beauty Guidelines

Aim for **visual scanability** and **enjoyment**—make the reader want to read it:

- Use **headers** (##, ###) liberally to break up content and create visual landmarks
- Convert prose paragraphs about "features" or "attributes" into **bullet lists** or **tables**
- Use ***bold*** for important terms, names, or conclusions; use *italic* for emphasis or subtle notes
- When 3+ items have attributes, prefer a **table** over repeated prose
- Use `inline code` for technical terms, function names, file paths, or specific values
- Use `code blocks` (```language) for multi-line examples, commands, or structured data
- Add blank lines between sections and lists for breathing room
- Consider **blockquotes** for definitions, warnings, key insights, or important asides

## Title

If the file has a title (top heading, frontmatter, or filename), evaluate whether a shorter or more specific title better fits the distilled content. Suggest or apply a better title if found. Report the title change (if any) in your summary.

## Output

Overwrite the file in place. State one line: what kind of filler was cut, any title change, and confirmation all facts are kept (e.g. "cut repetition and padding; title: 'Distill' → 'How to condense text'; all facts kept").
