# 🚀 TokenGuard Launch & Distribution Kit

> **Goal**: Position **TokenGuard** as the essential zero-dependency DevSecOps pre-commit secret scanner and Shannon entropy firewall with native OASIS SARIF v2.1.0 & fingerprinted baseline suppression.
>
> Live Repository: [https://github.com/umutgungorr/tokenguard](https://github.com/umutgungorr/tokenguard)  
> Case Study: [https://umutgungorr.com/projects/tokenguard](https://umutgungorr.com/projects/tokenguard)  
> PyPI Package: `pip install tokenguard-cli` / `uvx --from tokenguard-cli tokenguard`  
> GitHub Marketplace Action: `uses: umutgungorr/tokenguard@v1`

---

## 📅 High-Impact Launch Schedule (Timing Blueprint)

| Platform | Recommended Day & Time (EST) | Turkey Time (TRT / UTC+3) | Target Community & Tone |
|---|---|---|---|
| **Hacker News (Show HN)** | Tuesday or Wednesday, 08:30–09:00 AM EST | 15:30–16:00 | Security engineers, SREs, Python & zero-dependency enthusiasts |
| **Reddit (`r/Python`)** | Tuesday or Wednesday, 10:30 AM EST | 17:30 | Python builders, CLI developers, DevSecOps engineers |
| **Reddit (`r/netsec`, `r/devops`)** | Wednesday or Thursday, 09:30 AM EST | 16:30 | AppSec engineers, CI/CD architects, cloud security practitioners |
| **X / Twitter (Global)** | Simultaneous with HN (Tue 09:00 AM EST) | 16:00 | High-contrast terminal screenshots, entropy formula & SARIF demo |
| **LinkedIn (Global & TR)** | Wednesday, 11:00 AM EST | 18:00 | Engineering leads, CISOs, DevOps professionals |

---

## 1. 🟠 Hacker News (Show HN)

### Title Options
1. **Recommended**: `Show HN: TokenGuard – Zero-dependency pre-commit secret scanner with Shannon entropy and SARIF`
2. **Alternative A**: `Show HN: TokenGuard – Stop leaked AWS, OpenAI, and GitHub keys before they enter Git history`
3. **Alternative B**: `Show HN: TokenGuard – Sub-15ms pure Python secret firewall with line-independent baseline suppression`

---

### First Comment (OP Introduction — Post Immediately After Submitting)

```markdown
Hey HN! I built TokenGuard because every engineering team eventually faces the dread of an accidental credential commit—whether it's an `AKIA...` AWS key, an `sk-proj-...` OpenAI key, or a high-entropy webhook secret tucked inside a config file.

Once a secret touches remote Git history, `git revert` doesn't save you: automated scrapers index public commits in seconds, and rotating production keys + rewriting Git history (`git filter-repo`) burns hours of engineering time.

At the same time, adopting traditional secret scanners across existing repositories often fails because:
1. **Legacy & Mock Key Flood**: Running a scanner on an older repo flags 200 test fixtures and mock JWTs, causing teams to disable the check.
2. **Line-Number Fragility**: Baselines that track line numbers break every time someone adds an import at the top of a file.
3. **CI Log Re-Leaking**: Scanners that print the raw matched secret into GitHub Actions logs end up leaking the credential into CI build artifacts.
4. **External Binary / Dependency Bloat**: Installing heavy external binaries or 40 transitive packages in every Python dev environment slows down local pre-commit hooks.

TokenGuard (`tokenguard`) is a zero-dependency CLI written entirely in the Python Standard Library (`re`, `math`, `hashlib`, `json`, `argparse`, `subprocess`) designed to make secret prevention frictionless:

- 🛡️ **Hybrid Regex + Shannon Entropy Engine**: Combines high-precision signatures (`SEC-001` through `SEC-008` for AWS, GitHub PATs, OpenAI, Slack, PEM private keys, generic API keys, and JWTs) with mathematical Shannon entropy analysis ($H(X) = -\sum P(x_i)\log_2 P(x_i)$) to catch custom high-randomness tokens (`ENTROPY-001`).
- 🔒 **Automatic Boundary Masking**: Never echoes raw secrets to stdout or CI logs—values are automatically redacted (`ghp_************14TeR`).
- 📌 **Line-Independent SHA-256 Baselines (`.tokenguard.baseline`)**: Fingerprints findings using `SHA256(canonical_path : rule_id : masked_value)`—ignoring volatile line numbers so refactoring code never triggers false alarms on accepted test fixtures.
- 📊 **Native OASIS SARIF v2.1.0 (`--format sarif`)**: Plugs directly into GitHub Code Scanning Alerts with remediation guidance and confidence ratings.
- ⚡ **Zero Dependencies & <15ms Cold Start**: Runs anywhere on Python 3.9–3.14 via `uvx --from tokenguard-cli tokenguard --staged` or `pip install tokenguard-cli`.

Repo: https://github.com/umutgungorr/tokenguard
Case Study: https://umutgungorr.com/projects/tokenguard

Would love your feedback on the detection rules, entropy defaults, and baseline workflow!
```

---

## 2. 🔴 Reddit Launch Posts

### A. Subreddit: `r/Python`
**Title**: `I built TokenGuard: A zero-dependency Python pre-commit secret scanner with Shannon entropy detection, SHA-256 baselines, and SARIF v2.1.0 output`  
**Flair**: `Project` / `Showcase`

**Body**:
```markdown
Hi r/Python!

I wanted a fast, zero-dependency secret scanner that I could drop into any Python 3.9–3.14 repository (or run instantly via `uvx`) without pulling in heavy binaries or dozens of transitive packages.

So I built **TokenGuard** (https://github.com/umutgungorr/tokenguard):

### Highlights:
- **Zero External Dependencies**: 100% Python stdlib (`re`, `math`, `hashlib`, `json`, `pathlib`, `subprocess`). Cold startup in `<15ms`.
- **Hybrid Detection (`SEC-001`–`SEC-008` + `ENTROPY-001`)**: Detects AWS IAM/STS keys, AWS Secret Keys, GitHub PATs (`ghp_`, `github_pat_`), OpenAI keys (`sk-`, `sk-proj-`), Slack tokens (`xoxb-`), PEM/OpenSSH private keys, generic API assignments, JWTs, and unknown high-entropy secrets via Shannon entropy calculation.
- **Line-Number-Independent Baselines (`--update-baseline`)**: Generates `.tokenguard.baseline` using deterministic SHA-256 hashes of `(file_path, rule_id, masked_value)`. Editing lines above a test fixture won't break your baseline.
- **Safe Output Redaction**: Automatically masks secrets (`AKIA************4TE7`) so CI logs never leak credentials.
- **Native SARIF v2.1.0 (`--format sarif`)**: Uploads directly to GitHub Code Scanning Alerts.

Try it instantly without installing:
```bash
uvx --from tokenguard-cli tokenguard --staged
```

Or install via pip:
```bash
pip install tokenguard-cli
tokenguard --install-hook
```

Feedback and PRs for additional secret signatures are very welcome!
```

---

### B. Subreddit: `r/netsec` / `r/devops`
**Title**: `TokenGuard: Open-source, zero-dependency Git pre-commit secret firewall with line-independent baseline fingerprinting and SARIF v2.1.0`

**Body**:
```markdown
Hey folks,

Sharing **TokenGuard** (https://github.com/umutgungorr/tokenguard), a lightweight DevSecOps CLI and GitHub Action designed to stop credential leaks at the pre-commit and PR gate stages.

### Why we built it:
1. **Safe Redaction by Default**: Many scanners dump the offending line raw into CI stdout, turning a blocked PR into a CI log leak. TokenGuard masks secret interiors (`sk-p************9aBc`) across text, JSON, and SARIF outputs.
2. **Drift-Proof Baseline Suppression**: Legacy onboarding takes one command (`tokenguard --update-baseline`). Because fingerprints hash `canonical_path:rule_id:masked_value` rather than line numbers, code formatting and imports never invalidate your baseline.
3. **OASIS SARIF v2.1.0 Support**: Native integration with GitHub Advanced Security / Code Scanning (`tokenguard --format sarif -o results.sarif`).
4. **Zero Supply-Chain Footprint**: Pure Python standard library with zero third-party runtime dependencies.

GitHub Repository & Action: https://github.com/umutgungorr/tokenguard
```

---

## 3. 🌐 X / Twitter Launch Thread

```text
🛡️ Ever had a developer accidentally commit an AWS key, OpenAI token, or private key to Git?

Once it hits remote history, `git revert` won't save you.

Meet TokenGuard — a zero-dependency pre-commit secret scanner & Shannon entropy firewall for Python and CI/CD.

Pure stdlib. <15ms startup. Native SARIF v2.1.0.

🧵👇 (1/5)
```

```text
🔍 Hybrid Detection Engine:

Combines curated regex signatures (AWS IAM/Secret, GitHub PATs, OpenAI sk-proj, Slack xoxb, RSA/OpenSSH PEM keys, JWTs) with Shannon Entropy math:

H(X) = -∑ P(x) log₂ P(x)

Catches both known provider tokens AND custom high-randomness webhook secrets. (2/5)
```

```text
📌 Drift-Proof Baselines (.tokenguard.baseline):

Onboard legacy repos in 2 seconds:
$ tokenguard --update-baseline

TokenGuard hashes `path + rule_id + masked_value` (ignoring line numbers!), so adding imports at the top of a test file never breaks your CI baseline. (3/5)
```

```text
🤖 Built for Local Git Hooks & GitHub Code Scanning:

• Auto-masks secrets in logs (`ghp_************14TeR`)
• Native `--install-hook` & `.pre-commit-config.yaml` support
• Native `--format sarif` for GitHub Security tab alerts
• Zero external dependencies (Python 3.9–3.14) (4/5)
```

```text
⚡ Run it right now in any repo with zero install:

$ uvx --from tokenguard-cli tokenguard --staged

⭐ Star on GitHub: https://github.com/umutgungorr/tokenguard
📖 Case Study: https://umutgungorr.com/projects/tokenguard (5/5)
```

---

## 4. 💼 LinkedIn Post

```text
Accidental credential leaks in Git remain one of the most expensive—and preventable—security incidents in software engineering.

Once an AWS key, OpenAI token, or private SSH key is pushed to origin, reverting the commit isn't enough. You're stuck rotating production credentials under pressure and rewriting Git history.

Today I'm open-sourcing TokenGuard v0.2.0 🛡️ — a zero-dependency pre-commit secret vault and Shannon entropy firewall built entirely with the Python Standard Library.

What makes TokenGuard different:
✅ Hybrid Detection: High-precision signatures (AWS, GitHub, OpenAI, Slack, PEM Private Keys, JWTs) + Shannon Entropy calculation for unstructured secrets.
✅ Safe Log Masking: Automatically redacts secret values (`AKIA************4TE7`) so CI logs never become a secondary leak vector.
✅ Line-Independent Baselines: Uses SHA-256 fingerprinting without line-number coupling, allowing teams to grandfather test fixtures without brittle CI failures.
✅ Native SARIF v2.1.0: Integrates directly with GitHub Code Scanning Alerts.
✅ Zero Runtime Dependencies: Runs in <15ms across Python 3.9–3.14.

Try it immediately:
`uvx --from tokenguard-cli tokenguard`

🔗 GitHub: https://github.com/umutgungorr/tokenguard
📖 Case Study: https://umutgungorr.com/projects/tokenguard

#DevSecOps #AppSec #Python #OpenSource #CyberSecurity #GitHubActions #DeveloperTools
```
