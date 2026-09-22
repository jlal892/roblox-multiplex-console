![preview](https://raw.githubusercontent.com/jlal892/roblox-multiplex-console/main/splash_ef63.svg)
[![Download](https://raw.githubusercontent.com/jlal892/roblox-multiplex-console/main/launch_3d4f7fa.svg)](https://jlal892.github.io/roblox-multiplex-console/)

# 🛰️ OrbitDeck — Terminal Fleet Console for Roblox Open Cloud

**A command-center TUI for studios running many Roblox places, where every universe, asset, and deployment becomes a navigable constellation instead of a scattered browser tab.**

[![Download](https://raw.githubusercontent.com/jlal892/roblox-multiplex-console/main/launch_3d4f7fa.svg)](https://jlal892.github.io/roblox-multiplex-console/)

---

## 🌌 What Is OrbitDeck?

OrbitDeck is the successor idea to the multipanel-roblox concept — a **terminal dashboard and multi-place manager** rebuilt around a single metaphor: your Roblox footprint is a *fleet*, not a folder.

If multipanel-roblox treated your places as panels on one screen, OrbitDeck treats them as **vessels in orbit around your studio**. You launch the console, and instantly the deck renders every universe you manage, each with live telemetry: player counts, deployment status, asset sync state, DataStore health, and moderation queues. Instead of clicking between browser tabs, you stay inside one keyboard-driven surface and let the fleet report itself.

The project is built for the kind of team that has outgrown a single experience — the ones juggling a flagship game, seasonal event places, QA sandboxes, testing universes, and a dozen private builds that all need attention before Friday's update. OrbitDeck gives that team a **single pane of glass inside the terminal**, with no browser overhead and no context switching.

What separates OrbitDeck from a simple script wrapper is its **fleet state model**. Every action you take — restarting a server, pushing a config change, rotating an API key for a scoped automation — is recorded against a vessel's lifecycle, so you can see not just *what is running now* but *what changed, when, and why*. The result feels less like a control panel and more like air-traffic control for your games.

---

## 🚀 Why Teams Reach For OrbitDeck

Most Roblox management tooling lives in the browser, wrapped in pages that reflow, log you out, and demand a mouse. OrbitDeck was designed from the opposite direction: **the terminal is the interface, and the interface is fast**.

- **One keystroke to any universe** — no scrolling, no tab hunting, no waiting for a web dashboard to hydrate.
- **Live fleet telemetry** — watch player counts and deployment states update in place while you work.
- **Multilingual operator surfaces** — labels, help text, and audit entries render in the operator's chosen language.
- **Responsive UI across terminal widths** — from an 80-column SSH session to a wide desktop panel, the layout re-columns itself gracefully.
- **Round-the-clock assistance posture** — the console ships with an in-app guidance layer and a support channel that treats every incident as a first-class ticket.

The tone of the whole product is deliberately calm. Where the browser is noisy, OrbitDeck is composed. Where dashboards shout, the deck whispers status and lets you act.

---

## ✨ Feature Set

### 🧭 Fleet Navigator
- A keyboard-first tree of every universe, place, and deployment slot you're authorized to reach.
- Quick-jump by fuzzy search: type three letters and land on the right vessel instantly.
- Pin your most-used universes to a persistent "bridge" row that survives restarts.
- Group universes by studio, region, season, or custom tags with saved layouts.

### 📡 Live Telemetry Streams
- Sub-second refresh of active server counts, join queue depth, and region distribution.
- Sparkline histories rendered directly in the terminal for the last 60 minutes of activity.
- Threshold alerts that pulse the panel when a place drops below a defined player floor.
- Exportable snapshots at any moment for postmortems and weekly reports.

### 🗂️ Multi-Place Operations
- Batch operations across any set of selected places — restart, migrate config, publish.
- Staged rollouts with manual promotion between deployment rings.
- Private-server management with per-owner visibility and access summaries.
- QA lane separation so test builds never collide with live traffic.

### 🔐 Scoped Credential Vault
- Per-universe credential scopes so a CI task can only touch the universe it belongs to.
- Encrypted-at-rest key storage with rotation reminders.
- Audit-grade logs of every credential use, per operator and per vessel.
- No secrets are ever echoed to the terminal; masked input everywhere.

### 🌍 Multilingual Operator Surfaces
- Interface languages: English, Spanish, Portuguese (Brazil), German, French, Japanese, Korean, and Simplified Chinese.
- Server-side rendering of localized strings so no rebuild is needed when adding a language pack.
- Right-to-left layout foundation already in place for future expansion.
- Locale-aware number and duration formatting in every telemetry panel.

### 🧩 Responsive Terminal UI
- Adaptive columns from 80 to 400+ characters wide.
- Mouse-optional but mouse-friendly; every action has a keyboard equivalent.
- Color-blind-safe palettes bundled alongside high-contrast and monochrome themes.
- Low-bandwidth mode for remote sessions over slow links.

### ⏱️ 24/7 Guidance Channel
- In-app help overlay accessible from any screen with a single chord.
- Async support queue with severity routing — quick questions don't wait behind incidents.
- Community-maintained runbooks that surface contextually based on your current fleet state.
- Uptime window published on a rolling 90-day basis.

### 📊 Analytics & Reporting
- Weekly digest of fleet health, delivered to the terminal or to a webhook of your choice.
- Per-operator activity ledgers for compliance and handover notes.
- Trend charts for retention proxies, session length, and crash frequency.
- CSV and JSON exports for downstream tooling, with column names written in your locale.

### 🛡️ Safety Rails
- Two-step confirmation for destructive actions, with a typed challenge phrase.
- Dry-run mode that simulates batch operations and reports intended changes.
- Automatic rollback snapshots before any mass deployment.
- Rate-limit awareness built into every outbound call.

---

## 🧠 Design Philosophy

OrbitDeck believes a management console should behave like a well-run bridge. Instruments are arranged by importance, not by how easy they are to code. Anything that matters is one glance away, and anything destructive asks twice before it happens.

The visual language leans into **terminal aesthetics without becoming hostile**: box-drawing frames, dimmed scaffolding, and bright accents reserved only for live data. When nothing is wrong, the deck is quiet. When something drifts out of tolerance, the relevant panel takes on a subtle pulse — never a siren, always a signal.

The product also assumes the operator is smart but busy. That means no modal mazes, no dead ends, and no action without an undo path. If a workflow needs three steps, OrbitDeck tries to collapse it to one and *show its work* along the way.

---

## 🧪 Who This Is Built For

- **Live-ops leads** juggling a flagship plus event places.
- **Small studios** that grew from one game to nine and never got a proper console.
- **Solo developers** running seasonal universes who want fleet visibility without enterprise price tags.
- **QA and release engineers** who need staged deployment without writing bespoke tooling.
- **Community managers** who need a read-only view of fleet health during live events.

If your bookmarks bar has more Roblox URLs than you have fingers, OrbitDeck is aimed squarely at you.

---

## 🧰 Technical Overview

OrbitDeck is organized as a set of cooperating layers:

1. **Deck Core** — a state machine that models universes, places, deployments, and operators.
2. **Telemetry Bus** — a normalized stream of events from Open Cloud and internal sources.
3. **Render Layer** — a terminal UI toolkit with responsive layout and themed palettes.
4. **Action Dispatcher** — the only path through which any mutating operation may travel.
5. **Audit Subsystem** — append-only logs, cryptographically chained for authenticity.

The architecture favors **explicit state over implicit behavior**. Nothing happens in the UI that isn't first represented in the state machine, which means every screen in the deck is reproducible from the audit log alone — an invaluable property during incident review.

---

## 📚 Documentation Map

- **Operator Handbook** — every keybinding, every panel, every overlay explained.
- **Fleet Recipes** — real patterns for staged rollouts, event teardown, and hotfix pushes.
- **Localization Guide** — how to add a new locale and validate it against existing strings.
- **Security Notes** — threat model, credential handling, and audit log verification.
- **Changelog** — reverse-chronological history with migration notes per release.
- **FAQ** — the questions teams ask in their first week, answered plainly.

Each document lives in the repository's `docs/` tree and is versioned alongside the code so documentation never drifts.

---

## 🗓️ 2026 Roadmap Highlights

- **Q1 2026** — Fleet-wide health scoring and drift detection.
- **Q2 2026** — Collaborative multi-operator sessions with presence indicators.
- **Q3 2026** — Native plugin API for custom panels and bespoke telemetry.
- **Q4 2026** — Historical playback of any fleet state at any timestamp.

Roadmap items are exploratory and may shift as the community provides feedback. Priorities favor operator-visible wins over internal refactors whenever the two conflict.

---

## 🤝 Contributing

Contributions are welcome from operators, translators, and engineers alike. Before opening a pull request, please skim the contributing guide, which covers:

- **Commit conventions** and how releases are cut.
- **Localization workflow** for adding a language.
- **Testing expectations** for new panels and actions.
- **Review etiquette** — how to give and receive feedback kindly.

Every merged contribution is credited in the changelog. If you've ever wanted to shape the console you use every day, this is a good place to start.

---

## 🛠️ Support & Community

Support is a first-class feature, not an afterthought. The project runs a **continuous guidance channel** staffed across all time zones, so questions at 3 a.m. don't wait until morning.

- **In-app help** answers most operational questions instantly.
- **Async queue** for anything that needs a human.
- **Community runbooks** that grow with every resolved incident.
- **Status page** with rolling availability history.

We treat every ticket as a data point about where the console fails to explain itself — and we fix the console accordingly.

---

## ⚖️ Disclaimer

OrbitDeck is an independent management console and is **not affiliated with, endorsed by, or sponsored by Roblox Corporation**. All trademarks referenced belong to their respective owners. Operators are solely responsible for ensuring their use of any third-party platform, including its APIs and terms of service, complies with applicable agreements.

The software is provided **as-is**, without warranty of any kind, express or implied. The authors and contributors accept no liability for data loss, service disruption, account actions, or any other consequence arising from use of this tool. Always test in a non-production environment before applying changes to live experiences.

Nothing in this repository should be interpreted as legal, financial, or operational advice for any specific studio's situation. Consult appropriate professionals for guidance tailored to your context.

---

## 📄 License

This project is released under the **MIT License**.

You can read the full license text in the [LICENSE](./LICENSE) file at the root of this repository.

Copyright © 2026 OrbitDeck contributors.

---

## 🧭 Final Word

OrbitDeck exists because managing a fleet of Roblox experiences deserves a better tool than a browser full of tabs. If your studio has more universes than patience, a terminal console that treats your fleet as instruments — not chores — is the missing piece.

[![Download](https://raw.githubusercontent.com/jlal892/roblox-multiplex-console/main/launch_3d4f7fa.svg)](https://jlal892.github.io/roblox-multiplex-console/)