# The CA whose private key was "4": check your website's certificate 🔑

Everything from my Short about **eMudhra**, the Indian certificate authority whose intermediate CA keys were tiny numbers (one of them was literally `4`).

## What happened (short)
- **Who:** eMudhra, a listed Indian Certificate Authority (CA). In its global SSL/TLS business it issues the certificates behind the 🔒 in your browser.
- **The keys:** 8 intermediate CA private keys (ECC P-384) that should have been ~116-digit random numbers were values like **4, 56, 66, 115, 155, 156, 230, 237**, all below 256. Generated on 30 Apr 2025, they stayed exposed for ~17 months.
- **Discovery:** on 17 Oct 2026 a researcher ("Wayne") found them and signed *"We have a problem here"* with every key as proof.
- **Response:**
  - Chrome, Firefox, Apple and Microsoft blocked the intermediates (17–20 Oct), and eMudhra revoked them.
  - Mozilla removed the emSign ECC Root CA - G3.
  - CERT-In issued advisory CIAD-2026-0050.
- **22 Oct:** eMudhra announced it is **exiting the global SSL/TLS certificate business**.
- **India:** per MeitY and eMudhra, **Indian DSC and eSign users are not affected.**

## ✅ Is MY website affected?
You only need to act if your site's certificate was issued by **eMudhra / emSign**.

**1. Check in the browser:** click the 🔒 → "Connection is secure" → "Certificate is valid" → look at **Issued By**.

**2. Check from the terminal:**
```bash
echo | openssl s_client -connect yourdomain.com:443 -servername yourdomain.com 2>/dev/null \
  | openssl x509 -noout -issuer -subject -dates
```
If the issuer says **emSign** or **eMudhra**, replace the certificate.

**3. Replace it (free, ~5 minutes):**
```bash
# Ubuntu / Debian with nginx
sudo apt install certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
```
Or use a free certificate from your host or Cloudflare (Universal SSL). Any major CA works: Let's Encrypt, Google Trust Services, Sectigo, DigiCert…

**4. Update your apps and servers** so they pick up the browser and OS blocks:
- Python: `pip install -U certifi`
- Java: update to the patched JDK (CVE-2026-91403)
- OS: run the system updates (`apt upgrade`, macOS/Windows updates)

## 🧠 Lesson for developers
Never generate keys or passwords by hand or with a custom script you haven't tested. Use a proper CSPRNG or HSM, and **check the output**. A key you can guess is not a key.

## Sources
- Mozilla security blog: https://blog.mozilla.org/security/2026/10/20/protecting-firefox-users-following-the-compromise-of-emudhra-intermediate-certificates/
- Disclosure (Wayne): https://emudhra.we-have-a-problem.com/
- Scott Helme, "Eight Bits of Trust": https://scotthelme.co.uk/eight-bits-of-trust-emudhras-ca-keys-cracked-in-milliseconds/
- eMudhra exit notice: https://emudhra.com/en/press-release/emudhra-to-exit-global-ssl-tls-certificate-business
- The Register: https://www.theregister.com/security/2026/10/20/indian-certification-authority-emudhras-private-keys-compromised-one-of-them-was-the-number-4/5304312
- MeitY / DSC and eSign unaffected (Business Today): https://www.businesstoday.in/technology/story/impact-has-been-very-limited-meity-on-emudhra-security-incident-says-indian-dsc-and-esign-unaffected-562927-2026-10-21
- IFF letter: https://internetfreedom.in/a-private-key-with-the-value-4-iff-writes-to-emudhra-cert-in-and-meity-on-the-compromise-of-emudhras-certificate-authority-keys/
