# Challenge Notes

## Challenge Focus

This document records the workflow, observations, and outcome for the first completed challenge in the **Snyk CTF Event 2026**:

- **Challenge:** Did You Read The FAQ?
- **Difficulty:** Easy
- **Category area shown in the event UI:** Misc
- **Release date shown in the challenge UI:** February 12, 2026

This was the only challenge completed during the live event window (the "data vault" challenge was initiated but not completed as time ran out halfway through it), due to limited participation time caused by overlapping certification renewal work and other schedule constraints.

## Objective

The purpose of this challenge note is to document:

- how the challenge was approached
- what parts of the interface suggested the likely path
- how Burp Suite was used to inspect traffic
- how the flag was identified
- how the result was confirmed in the event UI

This file is written as retrospective documentation for an authorized capture-the-flag event. It is not intended as a general guide for testing unauthorized systems.

## Initial Challenge Read

The challenge title itself was the strongest early clue:

- **Did You Read The FAQ?**

The short instruction shown on the page reinforced that clue directly:

- **Make sure to read the FAQ!**

Because the challenge was marked **Easy**, the most reasonable interpretation was that the solution path would likely come from:

- opening the FAQ page directly
- reviewing client-visible FAQ content
- inspecting requests and responses associated with the FAQ page
- checking whether hidden or less obvious content appeared in network responses

Given the limited event time, this made the challenge a good first target.

## Starting State

The initial challenge page showed:

- `0 / 1 flag found`
- a single flag worth `100 XP`
- a blank submission field
- the challenge page available under the event interface

This established the baseline state before any traffic review or flag submission occurred.

## Workflow Summary

The solve path for this challenge can be summarized as:

1. open the challenge page
2. follow the clue by opening the FAQ page
3. inspect captured traffic in Burp Suite
4. identify the FAQ-related response
5. search the response for the flag string
6. recover the flag value
7. submit the flag in the challenge page
8. confirm challenge completion

## Step 1: Open the challenge page

The first step was to open the **Did You Read The FAQ?** challenge from the event dashboard.

At this point, the interface itself already suggested that the FAQ page mattered more than any deeper exploit path. There was no indication that the first step required brute force, fuzzing, or complicated state manipulation.

## Step 2: Open the FAQ page

The FAQ page was then opened directly in the browser.

The screenshots show the FAQ content including general event information such as:

- what a CTF is
- how long the event lasts
- how to access the challenges
- whether individual participation is allowed
- who NahamSec is
- whether solutions would be provided later
- event support and CPE information

Reading the visible page alone was useful for following the challenge prompt, but it was not enough by itself. The more important step was to review the traffic associated with the page inside Burp Suite.

## Step 3: Review traffic in Burp Suite

Burp Suite Community Edition was used to inspect HTTP history while navigating the FAQ content.

The captured requests included FAQ-related endpoints such as:

- `/page/faq`
- `/pages/faq`

This mattered because browser-visible rendering and API-delivered content are not always identical. Reviewing the actual response body is often faster and more reliable than assuming the visible page contains all relevant information.

## Step 4: Inspect the FAQ response

Inside Burp, the relevant FAQ response was opened in the response viewer.

The screenshots show the response body being examined with a search for:

```text
flag
```

This revealed the flag content embedded in the response data.

## Step 5: Recover the flag

The flag recovered from the response was:

```text
flag{let_the_games_begin}
```

The Burp screenshot clearly shows the recovered value highlighted in the response body and reflected in the inspector selection pane.

## Step 6: Submit the flag

After recovering the value from the FAQ response, the flag was submitted through the challenge page.

The follow-up screenshots confirm the transition from the unsolved state to the completed state.

## Step 7: Confirm completion

The event UI confirmed the solve with:

- challenge status showing the flag as found
- `1 / 1 flag found`
- a completion dialog stating **Hub Completed**
- a total of `100 XP` for the challenge

This closed the challenge successfully.

## Why the Solve Worked

This challenge worked as an effective first solve because it rewarded basic web testing habits:

- trust the wording of the prompt
- follow the obvious clue first
- inspect browser traffic instead of relying only on rendered content
- search the response body directly when the clue strongly suggests hidden text or metadata

In other words, the challenge was not about deep exploitation. It was about careful reading and efficient use of the browser-plus-proxy workflow.

## Practical Notes

A few points made this challenge especially suitable given the time constraints:

- it was clearly labeled **Easy**
- the prompt was direct
- the FAQ page was easy to access
- Burp HTTP history made navigation and inspection fast
- searching the response reduced unnecessary guessing

This made it possible to secure at least one valid solve despite having only a short participation window before the event ended.

## Evidence Preserved in Screenshots

The current screenshot set preserves the full progression:

- opening the challenge page
- viewing the FAQ page
- reviewing captured FAQ requests in Burp
- locating the flag in the response
- submitting the flag
- receiving completion confirmation
- final leaderboard and completion proof

This is useful both for portfolio presentation and for maintaining an accurate record of the event workflow.

## Result

The final result for this documented challenge was:

- **Challenge completed successfully**
- **Points earned:** 100
- **Recovered flag:** `flag{let_the_games_begin}`

This solve also matched the final event outcome reflected elsewhere in the repository:

- **Total points earned:** 100
- **Challenges completed:** 1

## Constraints

This document reflects the actual solve path used during the event, but it also needs to be read in context:

- the event participation window was limited
- only one challenge was completed before the event ended
- the repository is retrospective documentation, not a live event notebook
- some intermediate exploratory clicks may not be individually documented if they were not necessary to explain the final path

## Documentation-Only Note

This repository is documentation-only and is not maintained as an active tool. This file exists to document an authorized CTF challenge workflow and preserve a professional record of the event.

## Related Files

- `README.md`
- `docs/environment-setup.md`
- `docs/ctf-preparation.md`
- `docs/lessons-learned.md`
