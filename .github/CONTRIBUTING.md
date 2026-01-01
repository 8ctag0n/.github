# CONTRIBUTION PROTOCOL // ZYB LABS

> **"Code is easy. Context is hard."**

Welcome to the 8ctag0n research facility. We do not accept "code dumps." We accept architectural improvements backed by rigorous documentation and visual evidence.

---

## 1. THE SPIRIT: SERIOUS TECH, JOYFUL EXECUTION

While we demand rigor in architecture and security, we reject sterility. Technology is a playground.

- **Have fun:** If you built something clever, show it off.
- **Be creative:** If a CLI command can print a cool ASCII banner, do it.
- **Celebrate:** If a feature works beautifully, capture that moment.

We build serious systems, but we enjoy the process. If it's boring, you're doing it wrong.

---

## 2. THE COMMITMENT TO CONTEXT

Every line of code you change has a ripple effect. You must prove you understand that ripple.

### Commit Standards
Commits are not just "save points"; they are historical records.
- **FORBIDDEN:** "fix bug", "wip", "update".
- **REQUIRED:** A full explanation of the *Why*.
- **RECOMMENDED:** ASCII diagrams or Mermaid logic in the commit body for complex logic changes.

```text
feat(circuit): implement constraints for blind signatures

- Introduced a new R1CS constraint for the blinding factor.
- Updated the ZK prover key generation to account for N+1 gates.
- RATIONALE: Previous implementation leaked trace information in edge case X.

Topology:
[Input] -> [Blinding Gate] -> [Hash] -> [Output]
```

### Pull Request Standards
A PR is a scientific paper proposing a change to the reality of the codebase.
1.  **Context is King:** If you cannot explain *why* this change exists in 3 sentences, do not open the PR.
2.  **Architecture First:** If you change the `kernel` or `circuits`, you MUST include a Mermaid diagram explaining the new flow.

---

## 3. VISUAL ARTIFACTS (HIGHLY RECOMMENDED)

We believe in **"Show, Don't Just Tell."**

If your contribution involves:
- Frontend/UI changes (`zyb-apps`)
- CLI output modifications (`zyb-cli`)
- A complex state transition simulation
- Something strictly "cool" or satisfying

**You are strongly encouraged to attach a video (MP4/WebM) or GIF/Image.**
*See example: [8ctag0n Pull Request #5](https://github.com/8ctag0n/13/pull/5#issue-3765903217)*

> **NOTE:** Keep it professional. Artistic expression is welcomed; obscenity is grounds for immediate banishment.

---

## 4. THE WORKFLOW

1.  **Fork** the repository.
2.  **Branch** with intent (`feature/new-zk-proof`, `fix/memory-leak`).
3.  **Hack**.
4.  **Test**. (Untested code is considered dead code).
5.  **PR**. Fill out the template completely.

**[ END OF PROTOCOL ]**