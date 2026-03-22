# livecaption_solution

# Windows 11 24H2 — Fix Live Captions Stuck (Offline Manual Install)

This guide shows how to fix Live Captions stuck on "Downloading language data" by installing the required speech component manually, without using Windows Update.

---

## When to use this

Use this method if:
- Live Captions is stuck downloading forever
- VPN or firewall blocks Microsoft services
- Windows Update is not working

---

## What this installs

This installs only what is required for Live Captions:

- Speech Recognition (required)
- No Text-to-Speech
- No full language pack
- No extra features

---

## Step 1 — Download required files

Go to https://uupdump.net/

Search for "Windows 11 24H2" and select the build that matches your system.

Choose your language (for example, en-US).

Select the option "Download using aria2 + convert".

Download the ZIP file, extract it, and run the file named:

uup_download_windows.cmd

Wait for the process to complete.

---

## Step 2 — Locate the speech package

After the download finishes, find the following file inside the extracted folder:

Microsoft-Windows-LanguageFeatures-Speech-en-us.cab

This is the only file needed for Live Captions.

---

## Step 3 — Install the speech package

Open Command Prompt as Administrator.

Run the following command (replace the path with your actual file location):

```bash
dism /online /add-package /packagepath:"C:\path\to\Microsoft-Windows-LanguageFeatures-Speech-en-us.cab"
```

---

## Step 4 — Register the capability

Run the following command:

dism /online /add-capability /capabilityname:Speech~~~en-US~0.0.1.0

If this step fails due to network issues, you can ignore the error because the files are already installed.

---

## Step 5 — Fix source error (if needed)

If you see an error like "source files not found", run:

dism /online /add-capability /capabilityname:Speech~~~en-US~0.0.1.0 /source:C:\path\to\cab_folder /limitaccess

---

## Step 6 — Restart your computer

Reboot your system.

---

## Step 7 — Launch Live Captions

Press:

Win + Ctrl + L

Live Captions should open instantly without downloading anything.

---

## Expected result

- Live Captions works immediately
- No download required
- Fully offline functionality

---

## Common mistakes

Do not use these packages:
- Basic
- OCR
- Handwriting
- TextToSpeech

Only use:
- LanguageFeatures-Speech

---

## Why this works

Live Captions depends on the Windows Speech Recognition capability.

By installing it manually, you bypass Windows Update and avoid issues caused by VPNs, firewalls, or broken system services.

---

## Final result

- Live Captions works without errors
- No dependency on internet
- Minimal installation size
- Stable and clean setup
