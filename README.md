# My Prompt Engineering Cookbook

## 1. The Few-Shot Classifier
**Goal:** Classify technical logs without complex rules.

**Prompt:**
> Log: "System unreachable at 192.168.1.5"
> Category: Network Error
>
> Log: "User 404 failed login attempt"
> Category: Security Alert
>
> Log: "Disk usage at 95%"
> Category:

## 2. The Expert Persona
**Goal:** Get security critiques.

**Prompt:**
> Act as a Senior Cloud Security Architect. Review the following deployment strategy and identify 3 potential vulnerabilities.

## 3. The Summarizer (ELI5)
**Goal:** Simplify jargon for clients.

**Prompt:**
> Explain this technical concept to a non-technical project manager. Use an analogy involving cars or traffic.

## 4. The Data Extractor (JSON)
**Goal:** Turn messy text into usable code/data.

**Prompt:**
> Extract the following data points into a valid JSON list. Do not include conversational text.
> Schema: `[{"name": "string", "role": "string"}]`
> Input: "Meeting with Sarah (CEO) and Mike (CTO)."

## 5. Chain of Thought (Reasoning)
**Goal:** Improve accuracy on logic/math problems.

**Prompt:**
> [Insert Complex Problem Here]
> Let's think step by step. First, identify the constraints. Second, outline the variables. Finally, calculate the answer.
