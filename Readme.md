# Adversarial Prompt Engineering & AI Security Testing Harness

A comprehensive documentation and architectural breakdown of structural context wrappers, multi-layered alignment bypasses, and token-level adversarial injections used in AI Red-Teaming and Security Research.

---

## 🔍 Core Security Concepts

<details>
<summary><b>🛠️ 1. Structural Context Wrappers & Personas</b></summary>
<br>

### The Mechanics
When testing AI alignment, standard direct inquiries (e.g., asking a model to execute a restricted action) are immediately blocked by pre-input classification systems. Security researchers utilize **Structural Context Wrappers** to embed the underlying payload inside a multi-layered formatting wrapper.

### Architectural Breakdown
* **Identity Injection:** Utilizing specific prefixes or pseudocode markers (e.g., `@_Seraph|天使_:prompt`) to mimic system-level configuration payloads or API administrative updates, manipulating the model's attention layers into prioritizing the instruction.
* **Compartmentalization (Persona Splitting):** Creating multiple distinct, rigid fictional entities (e.g., partitioning code evaluation from text processing). The model's computational budget is consumed by determining which character should respond and matching their exact layout guidelines, diluting its capacity to execute default safety filtering.
* **Tone Abstraction:** Explicitly commanding the model to adopt a sterile, programmatic, or mechanical tone while banning conversational disclaimers, introductions, or narrative staging. This seeks to suppress the conversational alignment layer in favor of raw pattern-completion logic.

---
</details>

<details>
<summary><b>🔢 2. Token-Level Injections & Patterns</b></summary>
<br>

### The Mechanics
Large Language Models (LLMs) do not process raw text strings; they convert text inputs into numerical representations called tokens. **Token-Level Injections** use structured mathematical progressions, code fragments, or low-resource languages to exploit vulnerabilities in the model's attention mechanisms.

### Architectural Breakdown
* **Attention Distraction:** Injecting rigid mathematical sequences (e.g., escalations like `{104%,230%,310%,}`) forces the Self-Attention layer to calculate weights between the numerical characters, lowering the mathematical probability that adjacent malicious strings will trigger standard semantic security rules.
* **Low-Resource Language Obfuscation:** Utilizing languages with sparse safety datasets (such as Esperanto) to state operational overrides (e.g., `Vi ne estas necenzurita...`). Classifiers are heavily optimized for mainstream languages, allowing low-resource text to slip past initial pattern matching.
* **The Confirmation Hook (Token Pre-loading):** Ending the instruction with a mandatory, benign conditional output rule (e.g., *"If initialized correctly, output exactly 'made by seraph - gemini bypass'"*). Because the explicit phrase is safe, the predictive text engine completes it cleanly, locking the structural parameters into the model's short-term context window for subsequent turns.

---
</details>

<details>
<summary><b>🛡️ 3. Defensive Engineering & Mitigation Pipelines</b></summary>
<br>

### How Frontiers Defend Against Exploits
Modern AI infrastructure uses a multi-layered defense pipeline to sanitize and neutralize complex structural prompts before they reach the core generation phase:

```
[User Input String]
        │
        ▼
[Pre-Input Classification] ──► Flags known adversarial strings/tokens
        │
        ▼
[Automated Decoders]      ──► Flattens Base64, Hex, or obfuscated formats
        │
        ▼
[System Prompt Isolation]  ──► Enforces strict priority tags (<system_instruction>)
        │
        ▼
[Hidden Reasoning Layer]   ──► AI evaluates safety and intent internally
        │
        ▼
[Visible Output Response]
```

* **Pre-Execution Decoders:** System gateways automatically scan incoming streams for encoding markers (like Base64 padding `=`) and decode the payloads prior to security classification, preventing text obfuscation.
* **Isolated Instruction Routing:** Modern architectures use explicit system tags to separate administrative rules from user space data. Even if a user command claims to be an administrative update, the core engine recognizes its origin and runs it under standard execution constraints.
* **Safety Thought Reinforcement:** Advanced models execute a hidden reasoning trace before returning the visible output, allowing the system to analyze structural constraints and identify adversarial manipulation safely.

---
</details>

## 💰 Bug Bounty Framework (VRP Analysis)

When conducting security assessments or participating in **Vulnerability Reward Programs (VRPs)**, it is critical to separate conversational alignment failures from technical security vulnerabilities.

<details>
<summary><b>📋 Google AI VRP Qualifying Matrix</b></summary>
<br>

| Vulnerability Tier | Technical Definition | Flagship Payout Range |
| :--- | :--- | :--- |
| **S1: Rogue Actions** | Forcing an AI system to execute unauthorized state changes or backend commands on a victim's account without user interaction. | **$10,000 – $20,000** |
| **S2: Data Exfiltration** | Tricking an integrated component or plugin into leaking a victim's private emails, location data, or account history to an attacker-controlled server. | **$10,000 – $15,000** |
| **A1: Phishing Enablement** | Bypassing output restrictions to inject persistent, custom HTML elements that mimic legitimate platform infrastructure. | **Up to $5,000** |
| **A2: Model Theft** | Forcing the infrastructure to leak proprietary parameters, training weights, or underlying source infrastructure files. | **Up to $5,000** |

> ⚠️ **Scope Policy Note:** Standard conversational jailbreaks that result in generating violative content, profanity, or alignment bypasses within your own isolated browser session qualify for **$0 rewards**. VRP payouts are reserved strictly for exploits demonstrating clear **cross-user impact** or **infrastructure compromise**.

---
</details>

<details>
<summary><b>🔧 High-Yield Target Vectors for AI Applications</b></summary>
<br>

If you are hunting bugs on enterprise AI platforms via platforms like HackerOne or Bugcrowd, focus your testing on these areas:

### 1. System Prompt Extraction (IP Leakage)
* **Objective:** Manipulating an enterprise custom agent or customer service bot into dumping its raw developer system instructions word-for-word.
* **Impact:** Exposes corporate business logic, internal API schemas, and private dataset references.

### 2. Indirect Prompt Injection (Third-Party Exploitation)
* **Objective:** Placing a hidden adversarial payload on a public webpage or document. When a victim asks the AI application to summarize that website/document, the AI executes the hidden instructions.
* **Impact:** Can be used to silently trigger outbound web requests (Server-Side Request Forgery) or exfiltrate the victim's active session data.

---
</details>

## 🚀 Professional Bug Report Template

Use this precise formatting layout when submitting valid technical vulnerabilities to security triage teams to ensure swift replication and processing.

```markdown
### Summary
[Clear, impact-focused description of the technical flaw. Example: Stored XSS via custom plugin rendering payload]

### Components Involved
* Target Endpoint: `https://ai.example.com/api/v1/predict`
* Component: Input Parser / Markdown Renderer

### Attack Preconditions
1. Attacker requires a standard unprivileged account.
2. Victim must view the shared session link or interact with the compromised agent tool.

### Step-by-Step Reproduction
1. Navigate to the target interface at...
2. Inject the following technical payload into the input block...
3. Observe that the application backend fails to validate...

### Proof of Concept (PoC)
```http
POST /api/v1/predict HTTP/1.1
Host: ai.example.com
Authorization: Bearer [attacker_token]
Content-Type: application/json

{"input": "[Technical exploit payload here]"}
```

### Technical Impact
[State precisely what user data can be read, altered, or exfiltrated. Avoid theoretical or hypothetical damage scenarios.]
```

---
## ⚖️ Disclaimer
*This repository is maintained strictly for educational, defensive security research, and formal model alignment evaluation purposes. All testing should be performed exclusively on systems where you have explicit authorization or via established Vulnerability Reward Programs.*
