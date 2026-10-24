# Your AI tool got hacked → $1,700 bill: protect your API keys 🔐

Everything from my Short.

## What happened (Oct 2026)
### 1. LiteLLM 1.107.0: malware inside the update
- On **21 Oct 2026**, malicious `litellm==1.107.0` builds were published to **PyPI and Docker Hub**. They were live for roughly 2 hours.
- The payload ran on every Python start. It **stole SSH keys, cloud credentials, browser passwords, CI/CD secrets and AI API keys**, and installed a **backdoor**.
- Wiz saw stolen credentials being abused **about 4.5 hours** later.
- **Last safe version: 1.106.2.**

### 2. OpenCode: API keys leaked
- An older OpenCode Console system was breached, exposing the AI API keys of about **1.4% of Console users**.
- Some users reported **hundreds of dollars, up to ~$1,700**, in overnight charges.
- The open-source app and CLI were not affected.

## ✅ Checklist
1. **Set a spending limit on every API key.**
   - OpenAI: Settings → Limits
   - Anthropic Console: Billing → Spend limits
   - Google AI Studio / Cloud: Billing → Budgets & alerts
2. **Delete old and unused keys.** Create one key per project so a leak stays small.
3. **Don't auto-update.** Wait a day for new releases, then pin versions:
   ```bash
   pip install "litellm==1.106.2"
   # in requirements.txt:  litellm==1.106.2
   ```
4. **Did you install LiteLLM 1.107.0?** Treat the whole machine as compromised:
   ```bash
   pip show litellm            # check the installed version
   pip install "litellm==1.106.2" --force-reinstall
   ```
   - Remove the malicious `.pth` / `sitecustomize.py` files from `site-packages` (see Datadog's guide below), or rebuild the environment.
   - From a **clean machine**, rotate: SSH keys, cloud credentials (AWS/GCP/Azure), GitHub tokens, browser-saved passwords, and every AI API key.
5. **Never keep keys in code.** Use a secrets manager or `.env` files that never get committed.

## Sources
- LiteLLM incident report: https://docs.litellm.ai/blog/security-incident-oct-21-2026
- The Hacker News: https://thehackernews.com/2026/10/litellm-compromised-in-supply-chain.html
- Wiz: https://www.wiz.io/blog/litellm-compromised-steals-credentials
- Datadog remediation: https://securitylabs.datadoghq.com/articles/litellm-compromised-pypi-docker/
- TechCrunch (OpenCode): https://techcrunch.com/2026/10/19/hackers-hit-ai-coding-tool-opencode-running-up-charges-on-users-ai-accounts/
