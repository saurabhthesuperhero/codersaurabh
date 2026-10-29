# Is a hidden app reading your SMS? The 2-minute phone checklist 📱🛡️

Everything from my Short "RTO_Challan.apk". Share it with your family.

## What's happening (Oct 2026)
Scam SMS and WhatsApp messages say things like *"RTO e-Challan ₹1,000 pending, pay or your licence will be suspended"*, *"PM-KISAN installment pending"* or *"Bank KYC update"*, and ask you to install an **.apk** file.

That app asks for **SMS** and **Accessibility** access. It then forwards every SMS you get, **bank OTPs included**, to the scammer's database. The money is gone before the OTP expires.

Those databases are often **Google Firebase** (free), so the traffic looks like normal Google traffic.

On **22, 23 and 26 Oct 2026**, India's **I4C** (Ministry of Home Affairs) sent Google takedown notices covering **149 Firebase databases** used by such scam apps. Their names mimicked PM-KISAN, RTO, HDFC, ICICI and IPPB, plus about 20 "admin panel" names. That is just one week. Earlier rounds covered **216 databases in one day** in September and **174** in early October.

## ✅ The 2-minute checklist (Android)
*Menu names differ a little by brand (Samsung, Xiaomi, Vivo, OnePlus…). Use the search bar in Settings.*

1. **Who can read your SMS?**
   Settings → search **"Permission manager"** → **SMS**. Only your Messages app (and apps you really trust) should be in **Allowed**. Anything strange: **Don't allow**.
2. **Who has Accessibility (full control)?**
   Settings → **Accessibility** → **Installed / Downloaded apps**. Turn **OFF** anything you don't recognise.
3. **Who can read your notifications?**
   Settings → search **"Notification access"**. Remove unknown apps (they can read OTPs from notifications too).
4. **Block APK installs.**
   Settings → search **"Install unknown apps"** → set **Chrome, WhatsApp, Files, Telegram** to **Not allowed**.
5. **Device admin apps.**
   Settings → search **"Device admin apps"**. Nothing unknown should be here.
6. **Play Protect scan.**
   Play Store → profile photo → **Play Protect** → **Scan**. Keep it **ON**.

## 🚨 Found a suspicious app?
1. Turn on **airplane mode** / switch off the internet.
2. **Uninstall** it. If it won't uninstall, remove it from Device admin apps first, or boot into **Safe mode**.
3. Call your bank on the number on the **back of your card** and block cards/UPI. Change your **UPI PIN** and net-banking password from a clean phone.
4. Call **1930** / file at **[cybercrime.gov.in](https://cybercrime.gov.in/)** right away.

## ✅ Official websites only
- **Traffic challan:** https://echallan.parivahan.gov.in
- **PM-KISAN:** https://pmkisan.gov.in
- **Bank apps:** only from the **Play Store / App Store**, never from a link.

## 📵 Report scam SMS / calls
**Sanchar Saathi – Chakshu:** https://sancharsaathi.gov.in/sfc/

## Sources
- I4C takedown notices to Google (Lumen DB 100795192, 101418971, 101418978), summary: https://ministryofcyberaffairs.com/news/i4c-targets-149-more-firebase-hosts-used-in-pm-kisan-bank-and-rto-scam-apps-3f73e000-9f85-47f4-995a-52e43b649f44
