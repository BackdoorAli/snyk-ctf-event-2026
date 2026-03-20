# Snyk CTF 2026 - DataVault Write-Up and Environment Preparation

## Author
https://github.com/BackdoorAli

## Overview

This repository documents my preparation process, lab configuration, and partial participation in the Snyk CTF event held on **February 12, 2026**. The challenge environment covered in this write-up is the **Fetch the Flag 2026** event, with a focus on the first completed challenge: **Did You Read The FAQ?**

Due to overlapping commitments related to renewing CompTIA and other certifications, along with pre-existing schedule conflicts, I only had approximately one hour available to actively participate before the event ended. Although this limited the depth of progress I could make during the live competition window, the experience was still valuable and enjoyable, and it provided a solid foundation for future CTF participation.

This repository is intended as a professional portfolio project that documents:

- the preparation of a dedicated Kali Linux VM for the event
- the configuration of proxy and interception tooling
- the workflow used to validate browser traffic through Burp Suite
- the initial challenge reconnaissance process
- the discovery and submission of the first flag
- lessons learned for future timed CTF events

## Participation Context

The CTF event page showed the competition window as:

- **Start:** February 12, 2026 at 5:00 PM
- **End:** February 13, 2026 at 5:00 PM

At the time of participation, I was balancing the event against certification renewal, work and other scheduling constraints. As a result, I focused on getting a clean environment ready, validating the web testing workflow, and solving at least one challenge before the event closed.

The team used during the event was:

- **Team name:** NotAlita
- **Members:** 1

## Objectives

The purpose of this repository is to document:

- creation and preparation of a dedicated Kali Linux CTF virtual machine
- configuration of Firefox for proxy-based testing
- FoxyProxy setup for traffic routing through Burp Suite
- validation of manual proxy settings and browser behavior
- challenge navigation and reconnaissance
- recovery of the first flag from the FAQ challenge
- post-event retrospective and future improvements

## Scope

This repository covers:

- CTF preparation and environment setup
- VM resource configuration in UTM
- browser and proxy tooling configuration
- Burp Suite interception and HTTP history review
- challenge entry and early-stage web reconnaissance
- documentation of the first solved flag path
- lessons learned from limited-time participation
- various screenshots from the second challenge "data vault" and other miscellanious screenshots

This repository does **not** provide a full competition solution set, since I only had time to complete one flag before the event concluded.

## Repository Structure

```
snyk-ctf-event-2026/
├── README.md
├── LICENSE
├── .gitignore
├── SECURITY.md
├── CONTRIBUTING.md
├── assets/
│   ├── screenshots/
│   │   ├── preparation/
│   │   ├── vm-proxy-browser-config
│   │   ├── data-vault-challenge-and-other-screenshots/
│   │   ├── did-you-read-the-faq-challenge/
│   │   └── final-results/
├── docs/
│   ├── environment-setup.md
│   ├── ctf-preparation.md
│   ├── challenge-notes.md
│   └── lessons-learned.md
```

## Environment Summary

The challenge workflow was prepared in a dedicated Kali Linux virtual machine running in UTM on ARM64.

### VM details

Based on the setup screenshots gathered, the environment included:

- **VM name:** `Kali CTF - Snyk`
- **Architecture:** ARM64 (aarch64)
- **System profile:** QEMU 9.1 ARM Virtual Machine
- **Memory allocation:** 6144 MiB
- **CPU cores:** 4
- **Tooling notes shown in VM description:** Burp, FoxyProxy, CA certificate, CTF tools, Docker, clipboard support

### Core software and tooling

- Kali Linux
- Firefox
- FoxyProxy
- Burp Suite Community Edition
- Burp CA certificate import for HTTPS inspection
- browser proxy validation through local loopback on `127.0.0.1:8080`

## Verified Preparation Workflow

### 1. Dedicated VM selection and tuning

A dedicated Snyk-focused Kali VM was created and maintained separately from other Kali states. The VM screenshots show the system profile and hardware allocation being reviewed in UTM before use, including architecture, memory, and CPU core allocation.

### 2. FoxyProxy profile creation

A FoxyProxy profile named **Burp** was created and configured to route browser traffic to:

- **Host:** `127.0.0.1`
- **Port:** `8080`
- **Type:** `HTTP`

This allowed Firefox traffic to be routed cleanly into Burp Suite during challenge interaction.

### 3. Firefox manual proxy validation

Firefox connection settings were manually configured to use:

- **HTTP Proxy:** `127.0.0.1`
- **Port:** `8080`
- **Also use this proxy for HTTPS:** enabled

This confirmed that the browser was prepared for interception and inspection through Burp.

### 4. Browser-side proxy activation

A separate screenshot shows the FoxyProxy browser menu with the **Burp** profile enabled, confirming that proxy routing could be toggled directly from the browser during testing.

### 5. Challenge access and navigation

Once the environment was ready, the browser was used to access the Snyk CTF interface and navigate to the **Fetch the Flag 2026** event page. From there, the **Did You Read The FAQ?** challenge was opened as the first target.

## Challenge Summary

The first documented challenge in this repository is:

- **Challenge:** Did You Read The FAQ?
- **Difficulty:** Easy
- **Release date shown in UI:** February 12, 2026
- **Category area shown in event UI:** Misc

The challenge prompt itself strongly suggested that the FAQ content should be reviewed, which made it a straightforward first target during a limited-time participation window.

## First Flag Workflow

### Step 1: Open the challenge

The challenge page for **Did You Read The FAQ?** was opened from the event dashboard.

### Step 2: Review FAQ-related traffic in Burp Suite

Burp Suite Community Edition was used to inspect HTTP history while interacting with the challenge site. The relevant requests included FAQ-related paths, including content served from the API and page endpoints.

### Step 3: Inspect response content

The Burp HTTP history and response viewer were then used to inspect the returned FAQ content. Searching the response for the term `flag` revealed the flag value embedded in the response body.

### Step 4: Recover the flag

The response content showed the recovered value:

```text
flag{let_the_games_begin}
```

### Step 5: Submit and confirm completion

The recovered flag was submitted through the challenge interface, and the challenge UI confirmed completion with a **Hub Completed** message and a found status for the challenge.

## Screenshots

The repository will include screenshots grouped by phase so the write-up remains readable and maintainable.

Planned screenshot categories:

- `assets/screenshots/preparation/`
- `assets/screenshots/vm-proxy-browser-config/`
- `assets/screenshots/data-vault-challenge-and-other-screenshots/`
- `assets/screenshots/did-you-read-the-faq-challenge/`
- `assets/screenshots/final results/`


## Documented Workflow

This project is organized to show the progression from preparation to execution:

1. prepare the dedicated Kali VM
2. review VM hardware allocation and environment layout
3. configure FoxyProxy for Burp
4. configure Firefox manual proxy settings
5. validate proxy routing through the browser
6. enter the Snyk challenge environment
7. inspect FAQ-related traffic in Burp Suite
8. recover the first flag from response content
9. submit the flag and confirm completion
10. document lessons learned for future events

## Lessons Learned

Even with limited participation time, the session provided useful takeaways:

- pre-event environment preparation matters
- a dedicated CTF VM reduces setup friction
- proxy validation should be completed before event start
- Burp Suite workflow speed matters in timed challenges
- easy flags can often be solved quickly by carefully reading prompts and inspecting application responses
- scheduling conflicts can limit performance just as much as technical difficulty

## Future Improvements

For future CTF events, I want to improve the following:

- prepare and validate the environment before the event opens
- maintain a reusable CTF-ready Kali snapshot
- keep Burp, FoxyProxy, Firefox, and certificate setup documented as a repeatable checklist
- allocate uninterrupted time for the live event window (definitely the most important part, but life be lifing sometimes :P)
- capture screenshots and notes in parallel while solving additional challenges

## Disclaimer

This repository is intended for educational and portfolio purposes only. All activity described here took place in the context of an authorised capture-the-flag competition environment.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
