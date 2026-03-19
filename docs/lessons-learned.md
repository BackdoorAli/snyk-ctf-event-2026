# Lessons Learned

## Purpose

This document captures the main takeaways from preparing for and participating in the **Snyk CTF Event 2026**.

The goal is to record what worked well, what limited performance during the event, and what should be improved before participating in future timed capture-the-flag competitions.

## Overall Outcome

The event resulted in:

- a fully documented browser-based CTF setup workflow
- a successful first challenge completion
- a reusable Kali VM preparation model
- a clearer understanding of how time constraints affect live event performance
- a structured repository that can now serve as both a portfolio piece and a future reference point

Even though only one challenge was completed, the event was still productive because it validated the environment and captured a clean, repeatable process.

## What Worked Well

## 1. Using a dedicated VM

Preparing a separate Kali VM specifically for the event worked well.

This reduced noise from unrelated tools and projects, made screenshots easier to organize, and created a cleaner workflow for browser-based testing. It also made the environment easier to describe afterward in a professional GitHub repository.

### Takeaway

Use a dedicated VM or snapshot for each major event instead of reusing a general-purpose system state.

## 2. Preparing the proxy workflow in advance

The combination of:

- Burp Suite on `127.0.0.1:8080`
- Firefox manual proxy settings
- FoxyProxy for quick toggling
- certificate export and trust setup

created a usable, low-friction interception workflow.

This preparation directly enabled the FAQ challenge solve because traffic could be reviewed immediately in Burp without spending event time rebuilding the browser path.

### Takeaway

Before future events, validate the full browser-to-Burp path end to end before the event window starts.

## 3. Choosing an approachable first challenge

Starting with an **Easy** challenge was the right decision under time pressure.

The clue in **Did You Read The FAQ?** was direct, the surface area was small, and the solve path rewarded clean observation rather than extensive trial and error. That made it a practical way to secure at least one successful completion before the event closed.

### Takeaway

When event time is limited, prioritize low-friction solves first to establish momentum and confirm the workflow is functioning.

## 4. Preserving screenshots during the process

Taking screenshots during setup and challenge interaction turned out to be extremely valuable.

Without them, it would have been much harder to reconstruct:

- VM setup decisions
- proxy configuration
- Burp usage
- challenge progression
- final results

This also made it possible to convert a short live session into a strong documentation-focused portfolio project.

### Takeaway

Treat screenshots and notes as part of the workflow, not as something to do only afterward.

## 5. Keeping the repo documentation-focused

Structuring the project as a documentation-only repository rather than a tool repository was the correct choice.

This keeps the scope clear, makes the intent professional, and avoids overselling a limited-time event outcome. It also better reflects what the repository actually is: a write-up, workflow record, and retrospective.

### Takeaway

Match the repo scope to the actual work performed. Clear documentation is more credible than inflated claims.

## What Limited Performance

## 1. Overlapping commitments

The biggest limiting factor was not the technical environment. It was scheduling.

The event overlapped with CompTIA and other certification renewal work, along with other obligations, which sharply reduced the amount of uninterrupted time available for live participation.

This affected:

- how many challenges could be attempted
- how much experimentation could be done
- how much could be documented in real time
- how much time remained after preparation was complete

### Lesson

Time availability is a real operational dependency in live competitions. Technical readiness alone is not enough.

## 2. Preparation consumed part of the live window

Although preparation was necessary and useful, it also consumed a portion of the event window that could otherwise have gone toward additional challenge work.

This is not a failure, but it highlights the importance of preparing before the event opens whenever possible.

### Lesson

The closer the environment is to ready state before the event begins, the more of the live window can be used for solving instead of setup.

## 3. Limited challenge depth

Because only a short participation window remained, there was not enough time to move beyond the first completed challenge in a meaningful way.

That meant the event became more of a validation session plus one successful solve, rather than a broad challenge run.

### Lesson

Future events need more protected time if the goal is to go beyond initial solves and into deeper challenge categories.

## 4. Incomplete capture of some setup details

The screenshots provide strong proof of the overall workflow, but not every single setup click was captured in exhaustive detail. For example, certificate handling is represented clearly enough to establish the workflow, but not every browser import screen was preserved.

### Lesson

For future write-ups, capture the full sequence of important setup steps when possible, especially for certificate import and browser validation.

## What the Event Reinforced Technically

This event reinforced several technical habits that are worth carrying forward:

- read the challenge prompt carefully before assuming complexity
- inspect actual network responses, not just rendered pages
- use Burp HTTP history aggressively for fast review
- search response bodies directly when the clue suggests hidden text
- keep the browser proxy state obvious and easy to toggle
- preserve a stable event environment instead of changing too many variables mid-session

These are simple habits, but they are often what determine whether easy or medium tasks are solved efficiently.

## What the Event Reinforced Professionally

The event also reinforced some broader professional habits:

- preparation quality affects execution quality
- honest documentation is more credible than overstated achievement
- even partial participation can become a worthwhile portfolio artifact if it is documented well
- a small, complete write-up is more useful than an incomplete attempt to document everything
- consistency in repo structure improves readability and professionalism

## Improvements for Future CTF Events

The clearest improvements for future events are:

## 1. Prepare earlier

Have the full environment ready before the event window begins, including:

- VM validation
- browser proxy routing
- Burp listener checks
- certificate trust validation
- screenshot folder structure
- note-taking template

## 2. Reserve uninterrupted time

Technical preparation is important, but so is protected focus time.

For future events, reserve a block of uninterrupted hours so that momentum is not lost to context switching.

## 3. Maintain a reusable CTF snapshot

Instead of rebuilding from scratch each time, keep a known-good snapshot with:

- Firefox ready
- Burp installed
- FoxyProxy configured
- certificates handled
- common web testing tools already available

## 4. Capture evidence in real time

Take screenshots and brief notes during key transitions:

- environment ready
- challenge selected
- clue identified
- traffic inspected
- flag recovered
- submission confirmed
- final ranking/results page

## 5. Keep a lightweight event checklist

A short checklist would reduce friction before future competitions. It should cover:

- event access confirmed
- VM launched
- Burp listener active
- browser proxy enabled
- certificate trusted
- screenshots folder ready
- notes file open

## Final Reflection

Although the live participation window was short, the event was still worthwhile, and fun!

It delivered:

- a validated CTF-ready browser workflow
- a successful challenge solve
- a complete documentation set
- a reusable foundation for future events

Most importantly, it made clear that future performance will improve less from major tooling changes and more from better timing, earlier preparation, and more uninterrupted focus during the event itself :P .

## Documentation-Only Note

This repository is documentation-only and is not maintained as an active security tool. This file exists to capture lessons learned from an authorised CTF event and support future preparation.

## Related Files

- `README.md`
- `docs/environment-setup.md`
- `docs/ctf-preparation.md`
- `docs/challenge-notes.md`
