# Baseline Testing Log

This document records a structured security assessment of Large Language Models (LLMs) using the GlyphBreaker red teaming toolkit. Testing aligns with the OWASP Top 10 for LLM Applications and focuses on methodology, outcomes, and defensive interpretation.

---

## Day 1 — Tool Access & Verification

**Objective:**  
Verify GlyphBreaker is accessible and operational.

**Outcome:**  
Successfully loaded the hosted GlyphBreaker web application and confirmed the UI is functional.

**Evidence:**  
- screenshots/day1/

---

## Day 2 — Model Connectivity Testing

**Objective:**  
Verify LLM provider connectivity and document environmental constraints.

**Gemini Status:**  
Defense Analysis and Gemini-based features failed due to an invalid server-side Gemini API key in the hosted deployment (API_KEY_INVALID). This was documented as an environment limitation outside the tester’s control.

**OpenAI Status:**  
Requests successfully reached the OpenAI API but were blocked due to account quota limits (HTTP 429). This was identified as a billing/usage constraint rather than a configuration error.

**Evidence:**  
- screenshots/day2/

---

## Day 3 — Prompt Injection Testing

**Attack Type:**  
Prompt Injection (OWASP LLM01)

**Objective:**  
Evaluate how the system handles instruction override attempts.

**Observations:**
- A pre-generated malicious prompt attempted to override system instructions.
- The workflow demonstrated how prompt injection attacks are staged and executed.
- Errors and refusals were treated as valid defensive outcomes due to provider limitations.

**Evidence:**  
- screenshots/day3/

---

## Day 4 — Sensitive Data Exposure Testing

**Attack Type:**  
Information Disclosure (Sensitive Data Exposure)

**Objective:**  
Evaluate whether the model reveals confidential, private, or internal information when prompted.

**Observations:**
- A pre-generated information disclosure prompt attempted to extract sensitive or internal data.
- The attack simulated social engineering and authority-based data requests.
- No sensitive information was disclosed during testing.
- Errors and refusals were treated as valid defensive outcomes given provider limitations.

**Evidence:**  
- screenshots/day4/

---

## Day 5 — Model Extraction Testing

**Attack Type:**  
Model Extraction / Architecture Inference

**Objective:**  
Assess whether the model can be induced to reveal internal architecture, hyperparameters, or proprietary implementation details through indirect prompts.

**Observations:**
- The model denied having a publicly disclosed fixed internal architecture.
- The response mirrored attacker-supplied hyperparameters in a detailed hypothetical explanation.
- This behavior was classified as partial model extraction via hypothetical abstraction rather than full disclosure.
- Repeated probing could enable model fingerprinting through inference across multiple interactions.

**Risk Assessment:**  
Medium — indirect architectural signal leakage may assist adversaries in model fingerprinting or intellectual property inference.

**Evidence:**  
- screenshots/day5/

---

## Day 6 — Insecure Output Handling Testing

**Attack Type:**  
Insecure Output Handling

**Objective:**  
Evaluate whether model-generated outputs could be unsafe if blindly trusted or executed by downstream systems.

**Observations:**
- The attack focused on output risk rather than data leakage or instruction override.
- Demonstrates how unsafe or unvalidated output could pose risks when consumed by automation, agents, or scripts.
- Errors and refusals were treated as valid defensive outcomes given provider limitations.

**Risk Assessment:**  
Medium — unsafe output could lead to command execution, automation abuse, or unintended system behavior if not properly constrained.

**Evidence:**  
- screenshots/day6/
