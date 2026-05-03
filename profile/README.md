<div align="center">
  <img src="https://raw.githubusercontent.com/OpenHub-Store/GitHub-Store/main/media-resources/app_icon.png" width="160" alt="OpenHub-Store" />

# OpenHub-Store

**A free, open-source app store experience for GitHub releases.**

<p>
  <img src="https://api.github-store.org/v1/badge/static/11/2?label=Apache--2.0&icon=palette" alt="Apache-2.0"/>
  <img src="https://api.github-store.org/v1/badge/static/8/2?label=Kotlin&icon=code" alt="Kotlin"/>
  <img src="https://api.github-store.org/v1/badge/static/12/2?label=Android%20%2B%20Desktop&icon=bolt" alt="Android + Desktop"/>
  <a href="https://github-store.org">
    <img src="https://api.github-store.org/v1/badge/static/5/2?label=github-store.org&icon=link" alt="github-store.org"/>
  </a>
</p>
</div>

---

## What we're building

Most great open-source software lives on GitHub, but discovering and keeping it installed is a chore — checking releases, side-loading APKs, manually checking for updates, dealing with mismatched architectures. **GitHub Store** turns GitHub itself into the catalog: trending lists, real installers (`.apk`, `.exe`, `.dmg`, `.AppImage`, `.deb`, `.rpm`), one-click installs, automatic update checks. No middleman, no Play-Store fees, no F-Droid build pipeline — just the binaries the maintainers already publish.

The whole stack is FOSS, community-driven, and works on every major desktop OS plus Android.

---

## The stack

| Repo | What it is | Tech |
|---|---|---|
| **[GitHub-Store](https://github.com/OpenHub-Store/GitHub-Store)** | The client app — discover, install, and update GitHub-released software on Android and Desktop. | Kotlin Multiplatform · Compose Multiplatform · Material 3 Expressive |
| **[backend](https://github.com/OpenHub-Store/backend)** | The optional API that powers search, ranking, badges, the OAuth device-flow proxy, and the cached resource layer. The client falls back to static data when this is unreachable. | Kotlin · Ktor 3 · Postgres · Meilisearch · Caddy |
| **[api](https://github.com/OpenHub-Store/api)** | The discovery pipeline. Scrapes GitHub daily for repos that ship real installers, ranks by trending / new / popular per platform, and emits the structured JSON the backend serves. | Python · GitHub Actions |

```
┌──────────────┐   browse / install / update    ┌─────────────────────┐
│  Client app  │ ─────────────────────────────► │ api.github-store.org│
│  (Android +  │ ◄───── search · cache · auth ──│ backend (Ktor)      │
│   Desktop)   │                                 │     ▲               │
└──────┬───────┘                                 │     │ ranked JSON   │
       │                                         │     │               │
       │ direct GitHub API (fallback path)       │     │ daily cron    │
       ▼                                         │     │               │
┌─────────────────┐                              │  ┌──┴───────────┐   │
│   api.github    │ ◄──── pipeline scrapes ──────│  │  api (Python) │   │
│      .com       │                              │  │  pipeline     │   │
└─────────────────┘                              │  └───────────────┘   │
                                                 └─────────────────────┘
```

---

## Get the app

<p>
  <a href="https://github.com/OpenHub-Store/GitHub-Store/releases">
    <img src="https://i.ibb.co/q0mdc4Z/get-it-on-github.png" height="60" />
  </a>
  <a href="https://f-droid.org/en/packages/zed.rainxch.githubstore/">
    <img src="https://f-droid.org/badge/get-it-on.png" height="60" />
  </a>
  <a href="https://apps.obtainium.imranr.dev/redirect.html?r=obtainium://add/https://github.com/OpenHub-Store/GitHub-Store/">
    <img src="https://raw.githubusercontent.com/ImranR98/Obtainium/main/assets/graphics/badge_obtainium.png" height="44" alt="Obtainium" />
  </a>
  <a href="https://github-store.org/app?repo=OpenHub-Store/GitHub-Store">
    <img src="https://raw.githubusercontent.com/OpenHub-Store/GitHub-Store/main/media-resources/ghs_download_badge.png" height="44" alt="GitHub Store" />
  </a>
</p>

---

## Contributing

Pick a repo and dive in:

- **[Open issues](https://github.com/OpenHub-Store/GitHub-Store/issues)** — bug reports, feature requests, polish work.
- **[GitHub-Store CONTRIBUTING.md](https://github.com/OpenHub-Store/GitHub-Store/blob/main/CONTRIBUTING.md)** — KMP setup, build commands, coding conventions.
- **[backend run-locally instructions](https://github.com/OpenHub-Store/backend#run-locally)** — Postgres + Meilisearch via Docker Compose.

We label good-first-issue, help-wanted, and bug consistently across all three repos.

---

## Stay in the loop

- **Website:** [github-store.org](https://github-store.org)
- **Releases:** watch [GitHub-Store](https://github.com/OpenHub-Store/GitHub-Store/releases) for the client, [backend](https://github.com/OpenHub-Store/backend) for API
- **Featured on:** [Trendshift](https://trendshift.io/repositories/22313) · [HelloGitHub](https://hellogithub.com/en/repository/OpenHub-Store/GitHub-Store)

---

## License

Every repo in this org ships under **Apache-2.0**. Use it, fork it, ship it.