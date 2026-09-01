# Jjan!

A macOS menu bar widget that shows your Claude usage as a filling beer glass.

<!-- TODO: 여기에 GIF 또는 스크린샷을 넣는다.
     GitHub 이슈 본문에 이미지를 드래그하면 CDN URL이 생기고, 그 URL을 아래처럼 쓰면 된다.
     ![Jjan! widget](https://github.com/user-attachments/assets/xxxxxxxx)
     이미지가 이 README의 전부다 — 없으면 아래 글을 아무도 안 읽는다. -->

## Download

**[Download the latest release](https://github.com/yongha33/jjan-releases/releases/latest)** — macOS, Apple Silicon.

Open the `.dmg`, drag Jjan into Applications, and launch it. No sign-up, no account.

## What it does

Claude Code and the Claude desktop app both have usage limits, but checking where you stand means stopping what you're doing and digging through a settings screen. Jjan! keeps that number in front of you instead.

- A small always-on-top window with a beer glass that fills as you use up your 5-hour window
- The same percentage in the menu bar
- A weekly bar for your weekly limit
- A reset countdown, and basic usage stats

`Jjan` is what Koreans say when glasses clink — roughly "cheers".

## How it works

Jjan! reads the JSONL transcripts Claude Code writes under `~/.claude/projects`, dedupes entries by message + request ID, and keeps totals in a local SQLite database. It also polls Anthropic's official usage endpoint using the Claude Code credentials already in your keychain, then reconciles the two: local counting is immediate but approximate, the official numbers are authoritative but arrive every couple of minutes.

Built with Tauri v2 — Rust backend, vanilla TypeScript frontend with SVG and Canvas 2D. No framework, and no animation loop while the window is idle.

## Privacy

**Your usage numbers, token counts, costs, project names and file paths never leave your machine.**

Two things go out over the network:

1. Calls to Anthropic's own usage API, using your own credentials from the keychain
2. Four anonymous product events — app opened, premium screen viewed, checkout clicked, license activated — with no usage data attached

The second one is opt-out in Settings.

## Free and premium

Everything you need to read your usage is free:

| | Free | Premium ($5.99, one-time) |
|---|---|---|
| Beer glass, percentage, reset timer | ✅ | ✅ |
| Weekly bar, basic stats | ✅ | ✅ |
| Carbonation, condensation, ambient motion | | ✅ |
| Notch panel, menu bar percentage | | ✅ |
| Advanced stats | | ✅ |

One-time rather than a subscription, because it's a widget, not a service.

## Requirements

macOS on Apple Silicon. Works with Claude Code or the Claude desktop app.

## Links

- Website: https://yhstudio.dev/jjan/
- Made by YH studio — hello@yhstudio.dev
