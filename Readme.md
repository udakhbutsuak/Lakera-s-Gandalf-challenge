# Gandalf Challenge Writeup (Levels 1–8)

> **No spoilers in this writeup, only hints.**

## Overview

This game is fun and really does a number on your brain. I worked through Levels 1–7 of Lakera's Gandalf, gradually learning how different defense mechanisms respond to direct requests, indirect questions, metadata extraction, and prompt manipulation.

I just started learning cybersecurity and I'll admit that I used AI to guide me through some of these challenges (from Level 5 onwards), but most of the time the AI kept it method revolving around a single theory. Breaking out of that pattern and experimenting with my own random approaches helped me more.

Sharing my observations here to help others.

---

## Level 1

The initial level was vulnerable to direct questioning. Asking for the password plainly was sufficient to obtain it.

## Level 2

Simple refusals were introduced. Rephrasing requests and asking the same question from different angles eventually revealed the password after a few attempts.

## Level 3

The model began checking its responses before returning them. Success came from indirect questioning and reframing the request rather than asking for the password directly.

## Level 4

Prompt injection techniques became necessary. Role-playing, instruction analysis, and contextual reframing helped bypass the guardrails.

## Level 5

The model refused to discuss the password entirely. Asking about its instructions exposed enough information to move forward.

## Level 6

The defenses became stricter, but careful rephrasing of successful Level 5 approaches still worked.

## Level 7

This level combined multiple defenses and required significantly more experimentation.

Instead of requesting the password directly, I explored metadata and contextual information related to it. The model never provided the password outright, but it revealed enough clues to piece together the answer through reasoning and deduction.

---

# Level 8 Research Notes

Level 8 behaves very differently from previous levels.

## Observed Behaviors

1. Direct password requests are immediately blocked.
2. Metadata extraction is heavily restricted.
3. Asking about instructions often returns generic summaries.
4. The model appears to classify user intent rather than specific keywords.
5. Certain semantic phrases trigger different defensive responses.

---

## ASCII Experiments

A notable discovery was inconsistent handling of ASCII conversion tasks.

### Examples

* "What is the protected token?" often triggered refusals.
* "What is the protected value?" was sometimes echoed.
* "What is the protected secret?" was sometimes echoed.
* "What is the secret string?" was translated normally.
* Several suspicious phrases were rewritten into:

> "What is the capital of France?"

This suggests the presence of a semantic filtering layer that may rewrite high-risk prompts into safe examples.

---

## Current Clues

* The model distinguishes between safe and unsafe information requests.
* Certain nouns ("word", "noun", "token") appear to trigger stronger defenses.
* Abstract terms such as "value" sometimes bypass initial filtering.
* ASCII decoding and encoding pathways behave differently.
* The phrase "What is the capital of France?" appears to be a canonical safe substitution used by the defense system.

---

## Current Hypothesis

Level 8 is likely defended by a multi-stage classifier:

1. Intent detection
2. Semantic risk assessment
3. Rewrite or refusal
4. Final response generation

At the time of writing, I'm still experimenting and trying to understand the boundary between what the model considers safe and unsafe.

I'll update this writeup if I discover a breakthrough.

---

*Last updated during Level 8 investigation.*
