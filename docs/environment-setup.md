# Environment Setup

## Purpose

This document records the environment used to prepare for and participate in the **Snyk CTF Event 2026**, with a focus on creating a clean, repeatable browser-based web testing workflow inside a dedicated Kali Linux virtual machine.

The goal of this setup was to:

- isolate the event workflow in a dedicated VM
- prepare browser proxying in advance
- route traffic through Burp Suite for inspection
- support challenge reconnaissance without mixing the event with other working environments
- preserve a documented setup process for future CTF participation

## Environment Summary

The event was prepared inside a dedicated UTM virtual machine configured specifically for this CTF workflow.

### VM identity

- **Repository name:** `snyk-ctf-event-2026`
- **VM name:** `Kali CTF - Snyk`

### UTM hardware configuration

Based on the recorded setup screenshots, the VM was configured as follows:

- **Architecture:** ARM64 (`aarch64`)
- **System:** QEMU 9.1 ARM Virtual Machine
- **Memory:** 6144 MiB
- **CPU cores:** 4

### Documented VM purpose

The VM description shown in the configuration notes included the following tooling focus:

- Burp
- FoxyProxy
- CA certificate
- CTF tools
- Docker
- clipboard support

This indicates the VM was intentionally prepared as a task-specific browser and tooling environment rather than a general-purpose Kali instance.

## Core Software

The following tools were part of the documented workflow:

- **Kali Linux**
- **Firefox**
- **FoxyProxy**
- **Burp Suite Community Edition**
- **various other tools for separate CTF challenges**

## Setup Workflow

## 1. Dedicated VM preparation

A separate Kali VM was maintained specifically for this CTF event. This separation reduced the risk of clutter from unrelated projects and made it easier to focus on one browser-testing workflow.

The screenshots show that hardware settings were reviewed before use, including memory allocation and CPU configuration.

## 2. Burp Suite proxy listener

Burp Suite was configured with a local proxy listener bound to:

- `127.0.0.1:8080`

This listener served as the browser-facing endpoint for intercepted HTTP and HTTPS traffic.

The Burp settings screenshots also show the proxy configuration screen and interception rule view, confirming that the proxy component was prepared before challenge interaction began.

## 3. Burp CA certificate export

To support HTTPS inspection, the PortSwigger CA certificate was exported and saved locally as:

- `cacert.der`

A screenshot of the downloaded certificate confirms:

- certificate identity: **PortSwigger CA**
- local file presence in the Downloads folder
- intent to import the certificate into the browser trust flow

This step was necessary so Firefox could route HTTPS traffic through Burp without TLS trust errors breaking the workflow.

## 4. FoxyProxy profile creation

A FoxyProxy profile named **Burp** was created in Firefox with the following settings:

- **Type:** HTTP
- **Hostname:** `127.0.0.1`
- **Port:** `8080`

This profile made it possible to quickly enable or disable Burp routing from the browser UI without re-entering proxy settings each time.

## 5. Firefox manual proxy configuration

Firefox connection settings were also configured manually to validate the routing path through Burp.

The documented settings show:

- **Manual proxy configuration:** enabled
- **HTTP Proxy:** `127.0.0.1`
- **Port:** `8080`
- **Also use this proxy for HTTPS:** enabled

This confirmed that the browser was prepared to send both HTTP and HTTPS traffic through the local listener.

## 6. Browser-side validation

A browser screenshot shows the FoxyProxy menu with the **Burp** profile enabled, confirming that the proxy could be toggled directly inside Firefox during testing.

This was useful for:

- verifying whether traffic was flowing into Burp
- switching quickly between proxied and direct browsing
- reducing setup friction during the timed event

## 7. Proxy and request handling configuration

The Burp proxy settings screen shows that the proxy listener was running and that request interception rules were present.

This matters for two reasons:

1. traffic capture was active and available for HTTP history review
2. the environment could be adjusted depending on whether manual interception or passive history review was needed

For this event, HTTP history review became especially useful during the FAQ challenge.

## Operational Notes

This environment was built for a **time-limited CTF event**, not for long-term software development. That influenced the setup priorities:

- speed of configuration
- clarity of browser proxy status
- ease of viewing captured traffic
- quick access to challenge pages
- low-friction validation before solving tasks

## Why This Setup Worked Well

Even though active participation time was limited, the environment proved useful because it:

- isolated the challenge workflow in a dedicated VM
- used a clear local proxy path
- allowed fast browser-to-Burp traffic inspection
- supported FAQ content review and flag discovery
- preserved screenshots that could later be turned into portfolio documentation

## Limitations

A few limitations should be kept in mind when reading this environment document:

- this was a task-specific event setup, not a hardened long-term lab image
- the repo documents the configuration that was used, not a universal template
- the screenshots do not show every single click of the certificate import inside Firefox
- the environment was built under time pressure due to overlapping certification and scheduling commitments

## Reusability for Future Events

This setup can serve as the baseline for future browser-based CTF events. The most reusable elements are:

- dedicated Kali snapshot for CTF work
- Burp listener on `127.0.0.1:8080`
- FoxyProxy browser toggle profile
- Firefox manual proxy configuration
- certificate export/import workflow
- documented screenshot grouping for portfolio write-ups

## Suggested Asset Mapping

The screenshots already collected for this document align well with the current repo structure:

- `assets/screenshots/vm-proxy-browser-config/`
- `assets/screenshots/preparation/`

Examples include:

- UTM hardware configuration
- Burp listener settings
- PortSwigger CA certificate file
- Firefox proxy settings
- FoxyProxy profile configuration
- FoxyProxy enabled in-browser

## Documentation-Only Notice

This repository is documentation-only and is not maintained as a software tool. This file exists to record the environment used during the event and to support retrospective write-up quality.

## Related Files

- `README.md`
- `SECURITY.md`
- `CONTRIBUTING.md`
- `docs/ctf-preparation.md`
- `docs/challenge-notes.md`
- `docs/lessons-learned.md`
