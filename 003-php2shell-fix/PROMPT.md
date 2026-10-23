# The prompt

Paste this into Claude Code (or another coding assistant with shell access) on your server, or in your project folder. It asks before restarting anything or deleting files.

---

```text
You are on my server/project. Check whether I'm exposed to PHP2Shell (CVE-2026-109618, CVE-2026-109619).

1. Find every PHP runtime in use: CLI, php-fpm pools, Apache mod_php, Docker images/containers,
   cPanel MultiPHP. Report each one with its version.
2. Compare against the fixed releases: 8.5.12, 8.4.27, 8.3.36, 8.2.35. PHP 8.1 and older are
   end-of-life and must be upgraded. For distro packages (Ubuntu/Debian/RHEL), check the vendor's
   security notice, because the fix may be backported without a version change.
3. Show me the exact commands to update each runtime. Ask me before running anything that
   restarts services.
4. After I approve, update, restart, and verify the new versions.
5. Look for signs of compromise since 2026-10-17: new or modified .php files in web roots,
   unexpected cron jobs, unknown users or SSH keys, and unusually large POST requests to PHP
   endpoints in the access logs. Summarise what you find. Don't delete anything without asking.
6. If Cloudflare is in front of the site, confirm the site is proxied and that the origin only
   accepts traffic from Cloudflare IPs.

At the end, give me a short report: exposed / fixed / needs attention.
```
