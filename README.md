# Privacy Policy — Focus Guard

_Last updated: 2026-10-29_

Focus Guard is a browser extension that helps you stay focused while browsing by blocking distracting sites, tracking focus sessions, and (optionally) using AI to judge whether a page matches your goals or topics you want to avoid. This document explains what data the extension touches, where it goes, and what stays on your device.

## Summary

- Focus Guard does not operate any server of its own and does not collect, receive, or sell any of your data. There is no analytics or telemetry sent to the developer.
- All of your settings, lists, and history are stored locally in your browser (via the `chrome.storage` API), and are synced only through your own browser's built-in sync (e.g. Chrome Sync), if you have that enabled.
- The only network requests the extension makes go to **the AI provider you choose to set up** (any OpenAI-compatible provider, or a server on your own machine), and only if you set up the optional AI features yourself. Without that, Focus Guard makes no network requests at all.

## Data the extension stores locally

Stored in your browser's extension storage (`chrome.storage.sync` / `chrome.storage.local`), never transmitted to the developer:

- **Focus settings**: your focus goal, session start/end times, active template, custom templates.
- **Domain lists**: whitelist, blacklist, and conditional-block lists you configure, plus any "avoid topics" text you enter.
- **Template usage**: how often and when you last used each saved template, used to sort your templates.
- **Blocking log**: a local record of pages that were blocked or warned about (domain, type of block, time, and which button you chose), capped to the most recent 1,000 entries. It is used to tell whether you're seeing a site's warning for the first time.
- **Warning choices**: how often you chose "Stay Focused" for each kind of warning, and whether you declined the offer to close such pages automatically. Used to decide when to make that offer.
- **New tab preferences**: your choices for the new tab dashboard. Its background photos are bundled with the extension, so showing them makes no network request.
- **AI configuration**: the provider address and model you set up, whether AI checks are on, and which request format your model accepts. Your **API key is kept in `chrome.storage.local` only** — it is deliberately excluded from Chrome Sync so it stays on this device and isn't carried through Google's servers to your other devices.
- **AI interaction log**: prompts/responses sent to your configured AI provider for focus and avoid-topics checks are kept locally (capped to the most recent entries) so you can review or download them as a file from Settings > Customization > Advanced, for your own troubleshooting. This is never uploaded anywhere by the extension, and you can clear it at any time.

If you use Chrome's built-in sign-in/sync, data stored via `chrome.storage.sync` (settings and lists, but not your API key) is synced by Chrome across your own signed-in devices, subject to Google's Chrome Sync privacy policy. Focus Guard itself never sends this data anywhere.

## AI features (optional, off unless you configure them)

Focus Guard can use an LLM to judge whether a page aligns with your stated focus goal, or matches topics you've asked it to avoid. This only happens after you set it up in AI settings, agree to the data-sharing notice there, and a test request to your provider succeeds. You can turn it off again at any time, which also deletes your API key.

You choose the provider yourself — for example Groq, OpenAI, OpenRouter, Google Gemini, Mistral, a model running on your own computer (Ollama, LM Studio), or any other service with an OpenAI-compatible chat completions endpoint. There is no default provider.

While setting it up, the extension sends two kinds of requests to the provider you chose, using your API key: a request for the list of models it offers, and a short test question ("Reply with only the word Yes"). Neither contains any data about you or your browsing.

When active, for the page you're currently viewing the extension sends the following to whichever endpoint you've configured, using your API key:

- The page URL and domain
- The page title and meta description
- A short excerpt of on-page headings and paragraph text (truncated to a few hundred characters)

This is sent directly from your browser to the provider you configured, using your own API key — the developer of this extension never sees or receives this data. Your use of that provider is subject to its own privacy policy and terms. If you point the endpoint at a server running on your own machine, this data never leaves your device. No page content is sent unless you have set up and turned on the AI features.

## Other network requests

None. The preset blocking categories (e.g. "Social Media", "News & Media") and the new tab background photos are bundled with the extension, so using them makes no network request.

## Permissions

- **tabs** — to read the URL/title of the active tab so it can be checked against your lists and (if enabled) the AI check.
- **scripting** — to extract on-page text (headings/paragraphs) for the AI focus check, and to show in-page overlays/timers.
- **storage** — to save your settings, lists, and history locally as described above.
- **host permissions (all sites)** — required so blocking, overlays, and the focus timer can run on any site you visit, including for domains added to your own lists, and so the extension can reach the AI provider address you enter.

## Your control over your data

You can clear all extension data at any time via the extension's settings ("Clear All Domains" / reset options) or by removing the extension, which deletes all locally stored data. Because nothing is sent to a developer-controlled server, there is no external copy of your data to request or delete.

## Children's privacy

Focus Guard is not directed at children and does not knowingly collect data from children.

## Changes to this policy

If the data this extension touches changes (e.g. new features, new third-party services), this document will be updated and the "Last updated" date above will change.

## Contact

Questions about this policy: please open an issue at https://github.com/zurKreuzigungLinks/focus-guard-privacy/issues
