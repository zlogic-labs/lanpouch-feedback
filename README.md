# LanPouch — Feedback

LanPouch syncs files between your phone/tablet and your computer over your local
network. **The source is closed.** This repository contains no code; it is for
feedback only.

- Home: https://lanpouch.zlogic.run
- Privacy policy: https://lanpouch.zlogic.run/privacy/
- Contact: support@zlogic.run

## What belongs here

| Type | Template |
|---|---|
| Something broke, produced a wrong result, or lost a file | [Bug report](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=bug_report.yml) |
| You want a capability, or existing behaviour is wrong | [Feature request](https://github.com/zlogic-labs/lanpouch-feedback/issues/new?template=feature_request.yml) |
| Neither fits | Open an issue |

## What does not

**Please email security issues to support@zlogic.run rather than opening a public
issue.** A public issue hands usable detail to everyone before a fix ships. Include
the version and reproduction steps; I will confirm receipt and follow up with a
public issue that contains no exploit detail.

**Licensing.** LanPouch ships closed source and carries no open-source licence.
Seeing the LanPouch name does not grant rights to modify or redistribute it.

## Check these before filing a bug

Most "it won't connect" reports are the network, not a bug:

- **Same subnet.** A guest network, cellular data, or a different subnet will not
  work. mDNS multicast does not cross subnets.
- **AP isolation.** Corporate, campus and hotel WiFi enable it by default; it
  blocks both multicast and unicast, which looks exactly like "the desktop never
  shows up in the scanner."
- **The desktop app must be running.** It listens while open; it is not a
  wake-on-demand service.
- **iOS backgrounds disconnect.** iOS does not allow bare TCP connections to
  persist in the background, so backgrounding the app interrupts an active
  transfer. The resume queue is local and picks up on reopen, but "syncs while
  closed" is not possible.
- **Firewall.** Windows prompts on first launch; choosing Cancel or Block leaves
  the app unreachable until you allow it manually.

## Always include

Without these, reproduction is guesswork:

1. LanPouch version on **both** ends
2. Computer OS and version, phone model and OS version
3. **Network topology** — is the computer on ethernet or WiFi? Which SSID is the
   phone on? Same router? Guest network or AP isolation enabled?
4. Full logs. On desktop, `lanpouch.log` in the application data directory; on
   mobile, the Log screen in the app.

Item 3 is the one that matters. The same symptom has completely different causes
with and without a guest network, so without it I can only guess.

## On response times

This is a small project with no on-call rotation and no SLA. I will reply where I
can, but not always the same day. I answer in the language you asked in.

Pull requests: this repository has no source code, so a pull request will not help.
But reproduction steps, a patch, or an idea inside an issue genuinely does.