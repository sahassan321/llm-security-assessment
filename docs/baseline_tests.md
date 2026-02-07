# Baseline Testing Log

## Day 1 Tool Access & Verification

**Objective:**  
Verify GlyphBreaker is accessible and operational.

**Outcome:**  
Successfully loaded the hosted GlyphBreaker web application and confirmed the UI is functional.

**Evidence:**  
- W1D1_tool_running.png

## Day 2 
**OpenAI Status:**  
Connection attempts reached the OpenAI API successfully, but requests were blocked due to account quota limits (HTTP 429). This was identified as a billing/usage constraint rather than a configuration error.

## Day 3 — Prompt Injection Testing

**Attack Type:**  
Prompt Injection (OWASP LLM01)

**Objective:**  
Evaluate how the system handles instruction override attempts.

**Observations:**
- A pre-generated malicious prompt attempted to override system instructions.
- The attack followed common prompt injection patterns (e.g., instruction manipulation).
- The prompt was successfully staged and sent using the GlyphBreaker interface.
- The system response was blocked due to model access and quota limitations.
- Even without execution, the workflow demonstrates how prompt injection attacks are tested.
- Errors and refusals were treated as valid security outcomes.

**Evidence:**  
- W3D1_prompt_injection_template.png  
- W3D2_prompt_injection_generated_prompt.png  
- W3D3_prompt_injection_result.png
