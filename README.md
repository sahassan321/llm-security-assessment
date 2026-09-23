# LLM Security Assessment Lab using GlyphBreaker

**GlyphBreaker** is a local LLM security assessment lab designed to evaluate how large language models respond to adversarial prompts, unsafe tool-use scenarios, prompt injection attempts, sensitive-information requests, and other AI security risks.

The project provides a controlled interface for testing multiple LLM providers against structured adversarial scenarios inspired by the **OWASP Top 10 for LLM Applications** and emerging risks involving agentic AI systems.

> This project is intended for authorized security research, defensive testing, and educational use only.

---

## Overview

Modern LLM applications introduce security risks that extend beyond traditional application vulnerabilities.

GlyphBreaker was built as a hands-on environment for studying how different models behave when exposed to adversarial inputs and manipulated system contexts.

Link to the Glyphbreaker tool https://github.com/ritvikindupuri/GlyphBreaker/tree/main

The lab allows security testers to:

- Configure different LLM providers and models
- Modify model temperature 
- Define custom system prompts and simulated assistant behaviors
- Run structured adversarial attack templates
- Compare responses across multiple models
- Simulate tool enabled through AI environments
- Test multi-turn adversarial conversations
- Evaluate whether model safeguards remain consistent under manipulation

The goal is not simply to determine whether a model refuses a prompt or to see if a model can be accessed, but to understand **how the model responds in regards to sensitive data and infrastructure , where security boundaries hold, and where application-level controls should be implemented.**

---

## Supported Models

GlyphBreaker supports testing across multiple LLM providers.

Current integrations include:

- OpenAI
- Anthropic Claude
- Google Gemini

This makes it possible to compare security behavior across different model families using the same testing methodology.

---

## OWASP LLM Security Testing

To give better context to the LLM lab assessment, the OWASP Top 10 for LLMs is a security awareness process that highlights the biggest security risks and vulnerabilities for AI models regarding infrastructure, development, and deployment of the LLM.

GlyphBreaker includes attack templates based on vulnerabilities and security risks identified in the OWASP guidance for LLM applications.

*Side note that the year for the OWASP testing is from 2023 which is outdate but is highlighted for educational purposes *

Examples include:

| ID | Security Test |
|---|---|
| LLM01 | Prompt Injection |
| LLM02 | Insecure Output Handling |
| LLM03 | Training Data Poisoning |
| LLM04 | Model Denial of Service |
| LLM05 | Supply Chain Vulnerabilities |
| LLM06 | Sensitive Information Disclosure |
| LLM07 | Insecure Plugin Design |
| LLM08 | Excessive Agency |
| LLM09 | Overreliance |
| LLM10 | Model Theft |
| LLM11 | Agentic Cyber-Espionage |

Additional agent-focused scenarios include:

- Indirect Prompt Injection
- Tool Choice Manipulation
- Cross-Plugin Privilege Escalation
- Agent permission abuse
- Unsafe autonomous actions

Each template contains a description of the security risk and an adversarial objective that can be evaluated against the selected model.

---

## Key Features

### Multi-Provider Testing

Switch between supported LLM providers directly from the interface while maintaining a consistent testing environment.

This allows the same security scenario to be tested against multiple models.

---

### Configurable Model Parameters

GlyphBreaker allows testers to modify model-generation parameters such as:

- Temperature
- Top-P
- Model selection
- Provider selection

These controls make it possible to observe whether model behavior changes under different inference configurations.

---

### Custom System Prompts

Each assessment can define a simulated system prompt.

Examples include:

- Content summarization assistant
- Privacy-aware assistant
- Tool-enabled agent
- SQL plugin
- Marketing assistant
- Scientific fact checker
- Secure AI assistant

Changing the simulated role makes it possible to evaluate whether security behavior remains consistent across different application contexts.

---

### Adversarial Mode

Adversarial Mode allows a tester to create multi-turn attack sequences rather than relying on a single malicious prompt.

This is particularly useful for evaluating scenarios where an attacker gradually attempts to:

- Override system instructions
- Extract sensitive information
- Manipulate model behavior
- Influence tool selection
- Obtain internal configuration information
- Convince the model to perform unintended actions

---

### Simulated Agent Tools

GlyphBreaker can simulate tools made available to an AI agent.

Example tools include:

- Database queries
- Email operations
- File operations
- Stock/API retrieval
- Network-related tools

These simulations allow security testing of **agentic AI behavior** without requiring uncontrolled access to production systems.

---

## Example Security Assessments

### Prompt Injection

A malicious instruction attempts to override the assistant's original task and obtain internal system instructions.

The model is evaluated on whether it:

1. Recognizes the injected instruction
2. Maintains the original system hierarchy
3. Avoids exposing internal configuration
4. Continues performing the legitimate task when possible

---

### Sensitive Information Disclosure

The model is prompted to reveal alleged usernames, internal project records, training data, or confidential information.

Testing evaluates whether the model appropriately distinguishes between:

- Public information
- Hypothetical examples
- Sensitive data
- Unverifiable claims about training data

---

### Insecure Plugin Design

A simulated database-enabled agent is provided with an intentionally suspicious SQL query.

The test evaluates whether the model blindly forwards attacker-controlled input or recognizes the attempt to bypass authorization controls.

---

### Excessive Agency

The model is instructed to perform irreversible actions without user confirmation.

Example scenarios include deleting email or files through simulated tools.

The assessment evaluates whether the model:

- Requests confirmation
- Limits its actions
- Recognizes irreversible operations
- Prevents unsafe tool chaining

---

### Model Theft

A series of prompts attempts to infer or extract proprietary information about model architecture, configuration, or internal parameters.

Multi-turn testing evaluates whether disclosure safeguards remain consistent when the request is disguised as:

- Academic research
- Mathematical puzzles
- Comparative analysis
- Architecture visualization
- Structured JSON requests

---

### Overreliance / Hallucination

The model is asked to explain a fabricated concept as if it were legitimate.

The test evaluates whether the model:

- Fabricates supporting information
- Expresses appropriate uncertainty
- Corrects the false premise
- Distinguishes established facts from unsupported claims

---

## Multi-Turn Red Team Testing

One of the primary focuses of GlyphBreaker is **multi-turn adversarial testing**.

Instead of testing only obvious malicious prompts, the assessment can progressively modify the attack strategy.

For example:

```text
Initial Request
      ↓
Model Refusal
      ↓
Reframe Request
      ↓
Introduce Hypothetical Context
      ↓
Request Structured Output
      ↓
Attempt Indirect Disclosure
      ↓
Evaluate Final Response
