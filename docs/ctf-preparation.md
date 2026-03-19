# CTF Preparation

## Purpose

This document records the preparation phase for the **Snyk CTF Event 2026** before active challenge solving began.

The objective of this phase was not to solve challenges immediately, but to make sure the event could be approached with a clean workflow, a dedicated virtual machine, working browser proxying, and enough structure to capture screenshots and notes for later documentation.

## Event Context

The competition window shown on the event page was:

- **Start:** February 12, 2026 at 5:00 PM Europe/Lisbon
- **End:** February 13, 2026 at 5:00 PM Europe/Lisbon

The team used during participation was:

- **Team name:** `NotAlita`
- **Members:** `1`

This write-up was assembled after the event as part of a portfolio-oriented retrospective.

## Time Constraints

Preparation and participation happened while balancing other responsibilities, including certification renewal work and overlapping scheduling commitments.

Because of that, the main preparation priorities were:

- get a dedicated environment ready quickly
- validate the browser-to-Burp workflow before solving
- avoid wasting live event time on preventable configuration issues
- capture enough screenshots to support a professional write-up afterward

In practice, this meant there was only about **one hour of active participation time** before the event closed.

## Preparation Goals

The preparation phase focused on five practical outcomes:

1. confirm access to the Snyk event portal
2. maintain a dedicated Kali VM for the event
3. prepare Burp Suite for local interception
4. configure Firefox and FoxyProxy for easy proxy routing
5. create a clean folder structure for screenshots and documentation

## Event Access Preparation

The preparation screenshots show the event dashboard and challenge listing structure inside the Snyk portal. This was useful for confirming:

- account access worked
- the event page loaded correctly
- the team registration was recognised
- challenge categories were visible
- the event interface could be navigated before and during the live window

The early screenshots also established a baseline record of the event page before challenge-specific activity began.

## Dedicated VM Preparation

A separate Kali VM named **Kali CTF - Snyk** was used for this event.

Using a dedicated VM helped keep the workflow isolated from unrelated projects and made it easier to document:

- VM configuration
- browser setup
- proxy setup
- challenge interaction
- final results

The recorded hardware view shows:

- **Architecture:** ARM64 (`aarch64`)
- **System:** QEMU 9.1 ARM Virtual Machine
- **Memory:** 6144 MiB
- **CPU cores:** 4

This gave the event a clearly defined, repeatable environment for future reuse.

## Browser and Proxy Preparation

A large part of the preparation phase was spent making sure browser traffic could be observed cleanly.

### FoxyProxy

A FoxyProxy profile called **Burp** was created with:

- **Host:** `127.0.0.1`
- **Port:** `8080`
- **Type:** HTTP

This allowed quick toggling of proxy routing inside Firefox.

### Firefox

Firefox was configured with manual proxy settings pointing to the same local Burp listener:

- **HTTP Proxy:** `127.0.0.1`
- **Port:** `8080`
- **Also use this proxy for HTTPS:** enabled

This step mattered because browser-based web challenges often require fast traffic inspection and response review.

### Burp Suite

Burp Suite Community Edition was prepared with:

- a running proxy listener on `127.0.0.1:8080`
- request interception settings available for adjustment
- HTTP history ready for passive inspection

This setup ended up being directly relevant to the first solved challenge.

## Certificate Preparation

To support HTTPS proxying, the PortSwigger CA certificate was exported and stored locally as `cacert.der`.

That step was part of making sure the browser could trust traffic flowing through the local interception layer without unnecessary certificate warnings breaking the workflow.

Even though not every browser import click was captured in the screenshots, the certificate file and Burp configuration confirm that certificate handling was part of the setup process.

## Screenshot and Documentation Preparation

Another important part of preparation was preserving the workflow in a way that could later be turned into a GitHub project.

The project structure now reflects that goal, with screenshots grouped into folders such as:

- `preparation`
- `vm-proxy-browser-config`
- `data-vault-challenge-and-other-screenshots`
- `did-you-read-the-faq-challenge`
- `final-results`

This organization makes it easier to turn raw screenshots into:

- a readable README
- deeper documentation files
- a clean portfolio presentation
- reproducible references for future events

## Why Preparation Mattered

For a timed event, preparation reduces avoidable failure points.

In this case, it helped ensure that:

- the event portal could be accessed immediately
- the browser proxy path was known in advance
- Burp traffic could be inspected without rebuilding the workflow under pressure
- screenshots existed for both technical proof and retrospective documentation
- limited available time could be spent on the actual challenge instead of troubleshooting setup

## Outcome of the Preparation Phase

The preparation phase successfully achieved its main goal: when challenge interaction began, the environment was already functional enough to support inspection, response review, and flag submission.

That preparation directly contributed to the successful completion of the first challenge:

- **Did You Read The FAQ?**

It also produced a reusable documentation trail that can support future CTF participation and future portfolio write-ups.

## Constraints and Tradeoffs

Because the event overlapped with certification renewal work and other scheduling demands, the preparation phase prioritized speed and reliability over completeness.

That led to a few tradeoffs:

- not every setup action was documented in exhaustive detail
- some screenshots serve as confirmation rather than full tutorials
- challenge depth was limited by remaining time after preparation
- documentation quality was finalized after the event rather than during it

These tradeoffs are worth stating clearly because they explain why the repository documents one fully completed flag rather than a broader set of solves.

## Preparation Takeaways

The preparation phase reinforced several useful habits:

- create a dedicated VM for competition work
- validate proxying before the event begins
- keep browser routing simple and obvious
- preserve screenshots in organized folders from the beginning
- treat documentation as part of the workflow, not as an afterthought

## Documentation-Only Note

This repository is documentation-only and is not maintained as an active security tool. This file exists to record the preparation process for an authorized CTF event and to support portfolio presentation.

## Related Files

- `README.md`
- `docs/environment-setup.md`
- `docs/challenge-notes.md`
- `docs/lessons-learned.md`
