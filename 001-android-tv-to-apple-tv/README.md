# Turn your Android TV into an "Apple TV" with one Claude Code prompt 📺

Everything from my Short. Original project: **[Gathin23/cleanyourtv](https://github.com/Gathin23/cleanyourtv)** by [@gathint](https://x.com/gathint). All credit goes to him; star his repo ⭐

![Before / after](https://raw.githubusercontent.com/Gathin23/cleanyourtv/main/docs/card.jpg)

## What it does
- Finds your TV on Wi-Fi and connects over ADB
- **Disables** (doesn't uninstall) ad, telemetry and bloatware apps
- Installs a small, clean launcher that looks like Apple TV's home screen
- Gives you a restore script, so one command puts everything back

**Works on:** Android TV / Google TV (Xiaomi, Redmi, TCL, Hisense, Sony, OnePlus, Realme, Nvidia Shield…)
**Does NOT work on:** Samsung (Tizen), LG (webOS), most Fire TV

## Steps (Hindi + English)

**1. TV pe Developer options on karo / Turn on Developer options**
Settings → Device Preferences → About → **Build** pe 7 baar OK dabao (press OK 7 times)

**2. USB debugging on karo / Turn on USB debugging**
Settings → Developer options → **USB debugging** ON (Network/ADB debugging dikhe toh woh bhi ON)

**3. Laptop aur TV same Wi-Fi pe / Same Wi-Fi for laptop and TV**

**4. Claude Code kholo, prompt paste karo / Open Claude Code and paste the prompt**
Copy the prompt from [`PROMPT.md`](PROMPT.md), replace `<MODEL NAME HERE>` with your TV model.

**5. TV pe "Allow USB debugging?" → Allow**
Then answer Claude's questions: which apps you use, which 4 go in the dock.

**6. Kaam ho gaya? Debugging OFF karo / Done? Turn debugging OFF**

## ⚠️ Before you start
- Back up first. The prompt makes Claude save a restore script, so keep it.
- Disabling the update service also stops firmware/security updates until you re-enable it.
- Do it at your own risk. Read the original repo's [troubleshooting guide](https://github.com/Gathin23/cleanyourtv/blob/main/docs/TROUBLESHOOTING.md).

## Links
- Original repo: https://github.com/Gathin23/cleanyourtv
- Website: https://cleanyour.tv
- Original tweet: https://x.com/gathint/status/2111379569030939102
- TechCrunch: https://techcrunch.com/2026/10/19/people-are-using-ai-to-make-their-smart-tvs-dumb-again/

---
`PROMPT.md` is copied from Gathin23/cleanyourtv under the MIT License (© 2026 Gathin).
