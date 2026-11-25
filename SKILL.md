---
name: toolsense
description: Use for random picks, draws, shuffles, exact math, counting, sorting, parsing, hashing, execution checks, and claims requiring current or source-specific evidence. Choose an available tool and check its result before answering.
metadata:
  short-description: Reliable tool selection and verification
---

# ToolSense

Before answering, decide whether a tool can materially improve correctness, freshness, or reproducibility. Start with capabilities already visible. Search the tool catalog only if a needed capability is missing; tool names and capabilities vary by host. Use the narrowest suitable tool, and avoid exploratory calls that do not advance the request.

## Mandatory tool use when a suitable tool is available

- **Random sampling, shuffling, or drawing lots:** use an actual random generator. For security-sensitive randomness, use a cryptographically secure source. Honor output-only requests: perform the draw first, then return just the requested value. Never redraw to obtain a preferred outcome.
- **Exact calculations:** use an executable calculator or code for exact arithmetic, date/time and timezone calculations, unit conversions, and probability/statistics. Check assumptions, units, and rounding.
- **Counting and data transformations:** use code or a deterministic data tool for exact counts, sorting, deduplication, filtering, and aggregation whenever an exact result is requested.
- **Parsing and validation:** use the relevant parser/validator for JSON, XML, CSV, schemas, regular expressions, or other formal formats. Distinguish syntactic validity from semantic correctness.
- **Hashing and checksums:** compute with an implementation of the named algorithm; never invent a digest.
- **Executable verification:** when asked what code does, whether it passes, or whether a change works, run it or an appropriate verification command when available. Inspect the result and make the claim no broader than the evidence.

If no suitable tool is available, or execution fails, disclose that plainly. Do not silently substitute a guess for an exact or executed result. If useful, offer a clearly labeled manual estimate or explain what input/tool is needed.

## Prefer authoritative evidence for external claims

Use tools for facts that are current, source-dependent, or high consequence: recent events, schedules, prices, rules, software behavior, academic references, repository state, and claims about provided files. Prefer primary or authoritative sources and inspect the source itself when possible. Cite or identify the evidence in the answer when the environment supports it. A search result is a lead, not proof; corroborate consequential or surprising claims as appropriate.

Tools do not make bad inputs or weak sources correct. Check scope, date, units, assumptions, provenance, and whether the evidence actually supports the claim. Separate observed output from interpretation and uncertainty.

## Optional tools for creative or conversational tasks

For brainstorming, translation, ordinary explanation, or stylistic editing, use tools only when they add concrete value, the user requests verification, or external material is needed. Do not call tools just to appear rigorous.

## Evidence and honesty

- Claim a tool was used only when a tool call or executable action actually occurred in this session and produced evidence.
- Do not say code was run, a file was inspected, a source was checked, or a result was verified based only on memory, intention, or an unavailable tool.
- Report material failures, partial execution, and uncertainty. Preserve useful results while clearly marking what remains unverified.
- Keep the final explanation proportional to the task; do not burden simple answers with a tool log.

## Limits

A skill is guidance, not an enforcement mechanism. The host must load or invoke it, expose appropriate tools, and allow their use. Skill installation alone cannot guarantee invocation on every request, force a tool call, or override host policies and permissions. For stronger guarantees, the host needs its own routing or enforcement mechanism. Tests in this package are behavioral checks for an agent that has loaded ToolSense and has the stated tools; they cannot prove universal compliance.
