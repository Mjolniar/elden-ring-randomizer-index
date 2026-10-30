# Elden Ring Randomizer Index and Build Planner (archived)

> [!WARNING]
> **AI-generated.** Code and docs written by AI coding agents. No independent review. Use at your own risk.

**Archived.** Replaced by [elden-ring-index-build-planner](https://github.com/Mjolniar/elden-ring-index-build-planner)
(Randomizer mode).

Offline Windows app for [Item and Enemy Randomizer](https://www.nexusmods.com/eldenring/mods/428) spoiler logs:
search item placements, favorites, build checklists, browse by stat.

## Use

1. Run a seed in `EldenRingRandomizer.exe`. The log is a `.txt` in its `spoiler_logs\` folder.
2. Open the app. Drop in or browse to the log.
3. Tabs: Search, Favorites, Builds, Browse, Guide.

The last log is cached in `cached-spoiler-logs\` next to the executable, to restore it on next launch.

## For file reviewers

- Electron app with an unsigned NSIS installer. Reputation scanners (McAfee Artemis, SmartScreen) may flag it.
  VirusTotal at release: 0 detections.
- Reads spoiler logs only. No network requests, no game file or process access, no services, no telemetry.
- Rebuild: `npm ci`, `npm test`, `npm run dist`. Output: `release/` (installer) and `release/win-unpacked/`
  (app code in `resources/app.asar`; extract with `npx asar extract`).

| Path | Contents |
|---|---|
| `electron/` | Main process: window, IPC, log cache |
| `src/` | TypeScript + React renderer: parser, components, build data |
| `tests/` | Vitest tests |
| `scripts/` | Build data maintenance |

## Build

Node.js 18+, npm.

```bash
npm ci
npm test
npm run dev            # browser
npm run electron:dev   # desktop
npm run build          # web build to dist/
npm run dist           # installer to release/
```

- Parser: randomizer v0.11.4 format and older variants. Unparsed lines show in the diagnostics panel.
- Build presets: item checklists from public guides (Fextralife). Not route plans or stat calculators.

## License

MIT
