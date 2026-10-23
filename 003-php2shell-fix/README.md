# PHP2Shell: check & fix your website 💀🛡️

Everything from my Short. Two critical bugs **inside PHP itself** (CVE-2026-109618, CVE-2026-109619, CVSS 9.2) let attackers run code on a server **without logging in**. This affects PHP 5.4 to 8.5 (that's 14 years of releases), and roughly 70% of websites run on PHP: WordPress, Laravel, Drupal, Magento, cPanel…

> ⚠️ Updating WordPress or your plugins does **not** fix this. The bug is in the PHP runtime, so you have to update PHP itself.

## ✅ Safe versions
| PHP line | Fixed in |
|---|---|
| 8.5 | **8.5.12** |
| 8.4 | **8.4.27** |
| 8.3 | **8.3.36** |
| 8.2 | **8.2.35** |
| 8.1 / 8.0 / 7.4 or older | End-of-life. Upgrade to 8.2+ (only source patches exist for these) |

## Steps (Hindi + English)

**1. Version check karo / Check your version**
```bash
php -v                                            # CLI
php-fpm -v 2>/dev/null || ls /usr/sbin/php-fpm*   # FPM
apache2ctl -M 2>/dev/null | grep -i php           # mod_php (reported as highest risk)
docker ps --format '{{.Image}}' | grep -i php     # containers
```
Note: Ubuntu, Debian and RHEL packages sometimes include the fix without changing the version number. Check your distro's security notice for these CVEs.

**2. Update karo / Update**
```bash
# Ubuntu/Debian (example: PHP 8.3)
sudo apt update && sudo apt install --only-upgrade 'php8.3*'
sudo systemctl restart php8.3-fpm     # or: sudo systemctl restart apache2

# Docker
docker pull php:8.3-fpm               # then rebuild + redeploy your image
```
- **cPanel/WHM:** EasyApache 4 / MultiPHP → update PHP
- **Shared hosting:** change the PHP version in your hosting panel, or open a ticket with your host

**3. Ya Claude Code se karwao / Or let Claude Code do it**
Copy the prompt from [`PROMPT.md`](PROMPT.md) and paste it into Claude Code on your server or project. It finds every PHP runtime, checks the versions, asks before restarting anything, and looks for signs of compromise.

**4. Logs check karo / Check your logs**
Amazon saw exploit attempts from **17 Oct 2026**, four days before the patch. Look for new or changed `.php` files, unknown cron jobs or users, and unusually large POST requests from that date onward.

## 🛡️ Cloudflare users
Cloudflare turned on WAF rules for **every plan, including Free**, about 9 hours before the bugs were made public. To actually be covered by them:
- keep your site **proxied** (orange cloud)
- keep Managed Rules ON
- make your origin accept traffic **only from Cloudflare IPs**

Cloudflare itself calls this a **stopgap**. You still have to patch PHP.

## Links
- Cloudflare: https://blog.cloudflare.com/php-vulnerabilities-waf-protection/
- Wiz (AI found it): https://wiz.io/blog/php2shell-php-rce
- The Register (attacks before disclosure): https://www.theregister.com/cyber-crime/2026/10/22/hackers-pile-on-php2shell-as-aws-reveals-attacks-began-before-disclosure/5304749
- CERT-In alert (India): https://www.freepressjournal.in/tech/php-security-flaw-which-indian-websites-are-affected
- eMudhra CA keys (India): https://thehackernews.com/2026/10/eight-emudhra-ca-keys-compromised.html
- Node.js Oct 2026 security release: https://nodejs.org/en/blog/vulnerability/october-2026-security-releases
- Wikipedia: https://en.wikipedia.org/wiki/PHP2Shell

---
Only scan and fix servers **you own or are allowed to manage**.
